cmake_minimum_required(VERSION 3.10)
project(MyApp)

# Встановити крос-компіляцію для Windows
set(CMAKE_SYSTEM_NAME Windows)
set(CMAKE_SYSTEM_VERSION 10)

# Вказати шлях до компілятора MinGW
set(CMAKE_C_COMPILER x86_64-w64-mingw32-gcc)
set(CMAKE_CXX_COMPILER x86_64-w64-mingw32-g++)

# Встановити опції компіляції для статичної збірки
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -static -static-libgcc -static-libstdc++")

# Вказати шлях до встановленої SFML
set(SFML_DIR "/home/admin1/SFML-2.6.1_MinGW/lib/cmake/SFML")

# Указати, що використовуються статичні бібліотеки SFML
set(SFML_STATIC_LIBRARIES TRUE)
add_definitions(-DSFML_STATIC)

# Пошук та підключення SFML
find_package(SFML 2.6 COMPONENTS system window graphics REQUIRED)

# Додати директорію включення заголовкових файлів SFML
include_directories("/home/admin1/SFML-2.6.1_MinGW/include")

# Додавання виконуваного файлу
add_executable(MyApp main.cpp)

# Вказати директорії для лінкування
link_directories("/home/admin1/SFML-2.6.1_MinGW/lib")

# Підключення статичних бібліотек SFML і додаткових бібліотек залежностей
target_link_libraries(MyApp 
    /home/admin1/SFML-2.6.1_MinGW/lib/libsfml-system-s.a
    /home/admin1/SFML-2.6.1_MinGW/lib/libsfml-window-s.a
    /home/admin1/SFML-2.6.1_MinGW/lib/libsfml-graphics-s.a
    opengl32
    /home/admin1/SFML-2.6.1_MinGW/lib/libfreetype.a
    winmm
    gdi32
    ws2_32
    gdi32
    ole32
    winmm
    ws2_32
    jpeg
    freetype
    bz2
    png
    z
)
