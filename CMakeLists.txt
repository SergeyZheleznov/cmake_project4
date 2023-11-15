# CMakeList.txt : CMake project for CMakeProject3, include source and define
# project specific logic here.
# CMakeList.txt : CMake project for CMakeProject2, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.20)

project ("CMakeProject2")

# Add source to this project's executable.
add_executable (CMakeProject2 "main.cpp")

# Продключаем Catch2, после этого подключения в файле main-test.cpp можно не беспокоиться о пути к папке catch, поскольку эта папка уже подключена к нашему проекту
# подписанная синим test-build это папка для тестов. Где она находится, меня это не интересует, это внутреннее дело этой библиотеки. 
add_subdirectory(../catch2 test-build)

#здесь мы подключили ещё один исполняемый файл к нашему проекту, это файл main-test.exe, почему .exe не знаю. 
add_executable("main-test" "main-test.cpp")

# здесь мы подключили файл main-test к папке catch2, получается, что в этой файле у нас должны быть тесты
target_link_libraries("main-test" PRIVATE Catch2::Catch2)