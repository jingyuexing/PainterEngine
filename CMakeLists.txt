cmake_minimum_required(VERSION 2.8.0)
project(PainterEngine)

option(BUILD_WIN_EXE "build windows platform code" OFF)

option(BUILD_LINUX_EXE "build linux platform code" OFF)


# 此选项开启则将此项目安装到编译目录下的 PainterEngine 文件夹里 
# 如果关闭，则会安装在系统级路径下 如 linux的 、/usr/local win 的C盘下的 Programing Files 文件夹下

option(INSTALL_IN_PROJECT "" ON) 


if(INSTALL_IN_PROJECT)
    set(CMAKE_INSTALL_PREFIX ${PROJECT_BINARY_DIR}/PainterEngine)
endif(INSTALL_IN_PROJECT)


aux_source_directory(${PROJECT_SOURCE_DIR}/core CORE_SOUERCE_DIR)
aux_source_directory(${PROJECT_SOURCE_DIR}/kernel KERNEL_SOURCE_DIR)
aux_source_directory(${PROJECT_SOURCE_DIR}/architecture ARCHIVE_SOURCE_CODE)
add_library(painterEngine STATIC ${CORE_SOUERCE_DIR} ${KERNEL_SOURCE_DIR} ${ARCHIVE_SOURCE_CODE})

set(core_headers 
    core/PX_3D.h
    core/PX_AES.h
    core/PX_ANN.h
    core/PX_Arle.h
    core/PX_Base64.h
    core/PX_BaseGeo.h
    core/PX_Bitmap.h
    core/PX_BpNeural.h
    core/PX_Core.h
    core/PX_curve25519.h
    core/PX_Delaunay.h
    core/PX_Effect.h
    core/PX_Font.h
    core/PX_Hashmap.h
    core/PX_Huffman.h
    core/PX_ImageFilter.h
    core/PX_Linker.h
    core/PX_List.h
    core/PX_Log.h
    core/PX_MathTable.h
    core/PX_Memory.h
    core/PX_MemoryPool.h
    core/PX_MFCC.h
    core/PX_Packet.h
    core/PX_PointsMesh.h
    core/PX_Quadtree.h
    core/PX_Quicksort.h
    core/PX_rbtree.h
    core/PX_Sha256.h
    core/PX_Sound.h
    core/PX_SoundModule.h
    core/PX_String.h
    core/PX_Surface.h
    core/PX_Texture.h
    core/PX_TRaw.h
    core/PX_Tuning.h
    core/PX_Typedef.h
    core/PX_Vector.h
    core/PX_Wave.h
)
set(kernel_headers 
    kernel/PX_2dxCommon.h
    kernel/PX_3D_ObjData.h
    kernel/PX_Animation.h
    kernel/PX_Compiler.h
    kernel/PX_Json.h
    kernel/PX_Kernel.h
    kernel/PX_Lexer.h
    kernel/PX_LiveFramework.h
    kernel/PX_MODBUS.h
    kernel/PX_MQTT.h
    kernel/PX_Object.h
    kernel/PX_Object_Animation.h
    kernel/PX_Object_AutoText.h
    kernel/PX_Object_CheckBox.h
    kernel/PX_Object_Coordinate.h
    kernel/PX_Object_CursorButton.h
    kernel/PX_Object_Edit.h
    kernel/PX_Object_Explorer.h
    kernel/PX_Object_Image.h
    kernel/PX_Object_Label.h
    kernel/PX_Object_List.h
    kernel/PX_Object_Menu.h
    kernel/PX_Object_MessageBox.h
    kernel/PX_Object_Processbar.h
    kernel/PX_Object_Protractor.h
    kernel/PX_Object_PushButton.h
    kernel/PX_Object_RadioBox.h
    kernel/PX_Object_ScaleBox.h
    kernel/PX_Object_ScrollArea.h
    kernel/PX_Object_Selectbar.h
    kernel/PX_Object_TransformAdapter.h
    kernel/PX_Object_VirtualKeyboard.h
    kernel/PX_Object_Widget.h
    kernel/PX_Partical.h
    kernel/PX_Resource.h
    kernel/PX_Script_ASMCompiler.h
    kernel/PX_Script_Interpreter.h
    kernel/PX_Script_VM.h
    kernel/PX_ScriptCore.h
    kernel/PX_SoundLab.h
    kernel/PX_Sync.h
    kernel/PX_UI.h
    kernel/PX_World.h
)
set(architecture_headers 
    architecture/PainterEngine_Console.h
    architecture/PainterEngine_Executer.h
    architecture/PainterEngine_FoxLogo.h
    architecture/PainterEngine_Runtime.h
)
if(NOT DEFINED INSTALL_LIB_DIR)
    set(INSTALL_LIB_DIR lib)
endif()
if(NOT DEFINED INSTALL_BIN_DIR)
    set(INSTALL_BIN_DIR bin)
endif()
if(NOT DEFINED INSTALL_INCLUDE_DIR)
    set(INSTALL_INCLUDE_DIR include)
endif()

install(TARGETS painterEngine LIBRARY DESTINATION ${CMAKE_INSTALL_PREFIX}/lib)
install(FILES ${core_headers} DESTINATION ${CMAKE_INSTALL_PREFIX}/include/painterEngine/core)
install(FILES ${kernel_headers} DESTINATION ${CMAKE_INSTALL_PREFIX}/include/painterEngine/kernel)
install(FILES ${architecture_headers} DESTINATION ${CMAKE_INSTALL_PREFIX}/include/painterEngine/architecture)
