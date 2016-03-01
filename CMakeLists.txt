include(CheckFunctionExists)
include(CheckLibraryExists)

fips_begin_lib(simpleai)
    include_directories(. simpleai/src/ai simpleai/src/libs/lua)
    if (NOT FIPS_EXCEPTIONS)
        add_definitions(-DLUA_USE_LONGJMP -DAI_EXCEPTIONS=0)
    else()
        add_definitions(-DAI_EXCEPTIONS=1)
    endif()
    fips_dir(simpleai/src/ai)
    fips_files(
        AI.cpp AI.h
        AIRegistry.cpp AIRegistry.h
        IAIFactory.h
        ICharacter.h
        SimpleAI.h
    )
    fips_dir(simpleai/src/ai/group)
    fips_files(
        GroupMgr.cpp GroupMgr.h
    )
    fips_dir(simpleai/src/ai/server)
    fips_files(
        AIUpdateNodeMessage.h
        AIAddNodeMessage.h
        AIDeleteNodeMessage.h
        AIChangeMessage.h
        AICharacterDetailsMessage.h
        AICharacterStaticMessage.h
        AINamesMessage.h
        AIPauseMessage.h
        AISelectMessage.h
        AIStateMessage.h
        AIStepMessage.h
        AIStubTypes.h
        ChangeHandler.cpp ChangeHandler.h
        IProtocolHandler.h
        IProtocolMessage.h
        Network.cpp Network.h
        PauseHandler.cpp PauseHandler.h
        ProtocolHandlerRegistry.h
        ProtocolMessageFactory.cpp ProtocolMessageFactory.h
        ResetHandler.cpp ResetHandler.h
        SelectHandler.cpp SelectHandler.h
        Server.cpp Server.h
        StepHandler.cpp StepHandler.h
        UpdateNodeHandler.cpp UpdateNodeHandler.h
        DeleteNodeHandler.cpp DeleteNodeHandler.h
        AddNodeHandler.cpp AddNodeHandler.h
    )
    fips_dir(simpleai/src/ai/zone)
    fips_files(
        Zone.cpp Zone.h
    )
    fips_dir(simpleai/src/ai/filter)
    fips_files(
        IFilter.h
        SelectEmpty.cpp SelectEmpty.h
        SelectGroupLeader.cpp SelectGroupLeader.h
        SelectGroupMembers.cpp SelectGroupMembers.h
        SelectHighestAggro.cpp SelectHighestAggro.h
        SelectZone.cpp SelectZone.h
    )
    fips_dir(simpleai/src/ai/tree)
    fips_files(
        Fail.cpp Fail.h
        Idle.cpp Idle.h
        Invert.cpp Invert.h
        ITask.cpp ITask.h
        ITimedNode.cpp ITimedNode.h
        Limit.cpp Limit.h
        Parallel.cpp Parallel.h
        Print.cpp Print.h
        PrioritySelector.cpp PrioritySelector.h
        ProbabilitySelector.cpp ProbabilitySelector.h
        RandomSelector.cpp RandomSelector.h
        Selector.h
        Sequence.cpp Sequence.h
        Steer.cpp Steer.h
        Succeed.cpp Succeed.h
        TreeNode.cpp TreeNode.h
        TreeNodeParser.cpp TreeNodeParser.h
    )
    fips_dir(simpleai/src/ai/tree/loaders)
    fips_files(
        ITreeLoader.h
    )
    #fips_dir(simpleai/src/ai/tree/loaders/xml)
    #fips_files(
    #    XMLTreeLoader.cpp XMLTreeLoader.h
    #)
    fips_dir(simpleai/src/ai/tree/loaders/lua)
    fips_files(
        LUACondition.h
        LUA.cpp LUA.h
        LUAFunctions.h
        LUANode.cpp LUANode.h
        LUATree.cpp LUATree.h
        LUATreeLoader.cpp LUATreeLoader.h
        LUACondition.h
    )
    fips_dir(simpleai/src/ai/conditions)
    fips_files(
        And.cpp And.h
        ConditionParser.cpp ConditionParser.h
        False.cpp False.h
        Filter.cpp Filter.h
        HasEnemies.cpp HasEnemies.h
        ICondition.cpp ICondition.h
        IsCloseToGroup.cpp IsCloseToGroup.h
        IsGroupLeader.cpp IsGroupLeader.h
        IsInGroup.cpp IsInGroup.h
        Not.cpp Not.h
        Or.cpp Or.h
        True.cpp True.h
    )
    fips_dir(simpleai/src/ai/common)
    fips_files(
        IFactoryRegistry.h
        IParser.h
        IPrintable.h
        Math.h
        MemoryAllocator.h
        MoveVector.h
        NonCopyable.h
        Random.h
        String.h
        Thread.h
        ThreadPool.h
        ThreadScheduler.h
        Types.h
        Vector3f.cpp Vector3f.h
    )
    fips_dir(simpleai/src/ai/movement)
    fips_files(
        GroupFlee.h
        GroupSeek.h
        SelectionFlee.h
        SelectionSeek.h
        Steering.cpp Steering.h
        TargetFlee.h
        TargetSeek.h
        Wander.h
        WeightedSteering.h
    )
    fips_dir(simpleai/src/ai/aggro)
    fips_files(
        AggroMgr.cpp AggroMgr.h
        Entry.h
    )
    fips_deps(lua52)
    if (FIPS_LINUX)
        check_function_exists(__atomic_fetch_add_4 HAVE___ATOMIC_FETCH_ADD_4)
        if (NOT HAVE___ATOMIC_FETCH_ADD_4)
            check_library_exists(atomic __atomic_fetch_add_4 "" HAVE_LIBATOMIC)
            set(HAVE_LIBATOMIC False)
            if (HAVE_LIBATOMIC)
                fips_libs(atomic)
            endif()
        endif()
    endif()
fips_end_lib()
