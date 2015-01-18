fips_begin_lib(simpleai)
    include_directories(. simpleai/src/ai simpleai/src/libs/lua)

    fips_dir(simpleai/src/ai)
    fips_files(AI.cpp AI.h AIRegistry.cpp AIRegistry.h IAIFactory.h ICharacter.h SimpleAI.h)
    fips_dir(simpleai/src/ai/group)
    fips_files(GroupMgr.cpp GroupMgr.h)
    fips_dir(simpleai/src/ai/server)
    fips_files(AIChangeMessage.h AICharacterDetailsMessage.h AINamesMessage.h
        AIPauseMessage.h AISelectMessage.h AIStateMessage.h AIStepMessage.h
        AIStubTypes.h ChangeHandler.cpp ChangeHandler.h IProtocolHandler.h
        IProtocolMessage.h Network.cpp Network.h PauseHandler.cpp PauseHandler.h
        ProtocolHandlerRegistry.h ProtocolMessageFactory.cpp ProtocolMessageFactory.h
        ResetHandler.cpp ResetHandler.h SelectHandler.cpp SelectHandler.h
        Server.cpp Server.h StepHandler.cpp StepHandler.h Zone.cpp Zone.h)
    fips_dir(simpleai/src/ai/filter)
    fips_files(IFilter.h SelectEmpty.cpp SelectEmpty.h SelectGroupMembers.cpp
        SelectGroupMembers.h SelectHighestAggro.cpp SelectHighestAggro.h)
    fips_dir(simpleai/src/ai/tree)
    fips_files(Idle.cpp Idle.h Invert.cpp Invert.h ITask.cpp ITask.h ITimedNode.cpp
        ITimedNode.h Parallel.cpp Parallel.h Print.h PrioritySelector.cpp PrioritySelector.h
        Selector.h Sequence.cpp Sequence.h TreeNode.cpp TreeNode.h TreeNodeParser.cpp
        TreeNodeParser.h Wander.cpp Wander.h)
    fips_dir(simpleai/src/ai/tree/group)
    fips_files(FleeGroup.cpp FleeGroup.h FollowGroup.cpp FollowGroup.h)
    fips_dir(simpleai/src/ai/tree/loaders)
    fips_files(ITreeLoader.h)
    fips_dir(simpleai/src/ai/tree/loaders/lua)
    fips_files(LUACondition.h LUA.cpp LUAFunctions.h LUA.h LUANode.cpp
        LUANode.h LUATree.cpp LUATree.h LUATreeLoader.cpp LUATreeLoader.h)
    fips_dir(simpleai/src/ai/conditions)
    fips_files(And.cpp And.h ConditionParser.cpp ConditionParser.h False.cpp
        False.h Filter.cpp Filter.h HasEnemies.cpp HasEnemies.h ICondition.cpp
        ICondition.h IsCloseToGroup.cpp IsCloseToGroup.h IsGroupLeader.cpp IsGroupLeader.h
        IsInGroup.cpp IsInGroup.h Not.cpp Not.h Or.cpp Or.h True.cpp True.h)
    fips_dir(simpleai/src/ai/common)
    fips_files(Enum.h IFactoryRegistry.h IParser.h IPrintable.h
        Math.h MemoryAllocator.h MoveVector.h NonCopyable.h Random.h String.h Thread.h
        Types.h Vector3f.cpp Vector3f.h)
    fips_dir(simpleai/src/ai/movement)
    fips_files(Steering.h)
    fips_dir(simpleai/src/ai/aggro)
    fips_files(AggroMgr.cpp AggroMgr.h Entry.h)
    fips_dir(simpleai/src/libs/lua)
    fips_files(lapi.cpp lapi.h lauxlib.cpp lauxlib.h lbaselib.cpp lbitlib.cpp
        lcode.cpp lcode.h lcorolib.cpp lctype.cpp lctype.h ldblib.cpp
        ldebug.cpp ldebug.h ldo.cpp ldo.h ldump.cpp lfunc.cpp lfunc.h
        lgc.cpp lgc.h linit.cpp liolib.cpp llex.cpp llex.h llimits.h
        lmathlib.cpp lmem.cpp lmem.h loadlib.cpp lobject.cpp lobject.h
        lopcodes.cpp lopcodes.h loslib.cpp lparser.cpp lparser.h
        lstate.cpp lstate.h lstring.cpp lstring.h lstrlib.cpp
        ltable.cpp ltable.h ltablib.cpp ltm.cpp ltm.h luac.cpp luaconf.h
        lua.cpp lua.h lua.hpp lualib.h lundump.cpp lundump.h lvm.cpp
        lvm.h lzio.cpp lzio.h)
fips_end_lib()

