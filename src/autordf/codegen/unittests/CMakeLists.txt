INCLUDE_DIRECTORIES(
    "${PROJECT_SOURCE_DIR}/include"
    "${CMAKE_CURRENT_BINARY_DIR}"
)

ADD_EXECUTABLE(
    testcodegen
    TestCodeGen.cpp
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IAgent.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IDocument.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IGroup.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IImage.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/ILabelProperty.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IOnlineAccount.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IOnlineChatAccount.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IOnlineEcommerceAccount.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IOnlineGamingAccount.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IOrganization.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IPerson.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IPersonalProfileDocument.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IProject.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/rdfs/IResource.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/rdfs/IClass.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/owl/IThing.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/Agent.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/Document.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/Group.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/Image.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/LabelProperty.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/OnlineAccount.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/OnlineChatAccount.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/OnlineEcommerceAccount.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/OnlineGamingAccount.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/Organization.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/Person.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/PersonalProfileDocument.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/Project.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/rdfs/Resource.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/rdfs/Class.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/owl/Thing.cpp"
    "${CMAKE_CURRENT_BINARY_DIR}/foaftest/RdfTypeInfo.cpp"
)

TARGET_LINK_LIBRARIES(
    testcodegen
    autordf
    boost_system
    boost_filesystem
)

ADD_CUSTOM_COMMAND(
    OUTPUT
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IAgent.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IDocument.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IGroup.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IImage.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/ILabelProperty.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IOnlineAccount.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IOnlineChatAccount.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IOnlineEcommerceAccount.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IOnlineGamingAccount.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IOrganization.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IPerson.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IPersonalProfileDocument.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/IProject.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/rdfs/IResource.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/rdfs/IClass.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/owl/IThing.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/Agent.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/Document.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/Group.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/Image.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/LabelProperty.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/OnlineAccount.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/OnlineChatAccount.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/OnlineEcommerceAccount.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/OnlineGamingAccount.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/Organization.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/Person.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/PersonalProfileDocument.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/foaf/Project.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/rdfs/Resource.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/rdfs/Class.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/owl/Thing.cpp"
        "${CMAKE_CURRENT_BINARY_DIR}/foaftest/RdfTypeInfo.cpp"
    COMMAND "${CMAKE_CURRENT_BINARY_DIR}/../autordfcodegen" -o foaftest "${CMAKE_CURRENT_SOURCE_DIR}/foaf_20140114.rdf"
    DEPENDS "${CMAKE_CURRENT_BINARY_DIR}/../autordfcodegen"
)

ADD_EXECUTABLE(
    testmrd
    TestMrd.cpp
    ${CMAKE_CURRENT_BINARY_DIR}/AllInOne.cpp
)

TARGET_LINK_LIBRARIES(
    testmrd
    autordf
)

ADD_CUSTOM_COMMAND(
    OUTPUT
    ${CMAKE_CURRENT_BINARY_DIR}/AllInOne.cpp
    COMMAND "${CMAKE_CURRENT_BINARY_DIR}/../autordfcodegen" -a -n "mrd:http://www.ariadnext.com/ontologies/2015/MachineReadableDocument/1.0.0#" "${CMAKE_CURRENT_SOURCE_DIR}/MachineReadableDocument.owl"
    DEPENDS "${CMAKE_CURRENT_BINARY_DIR}/../autordfcodegen" "${CMAKE_CURRENT_SOURCE_DIR}/MachineReadableDocument.owl"
)
