cmake_minimum_required(VERSION 3.10)
project(CrowServer)

# ��������� �������� C++
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# ���������� vcpkg ����� ���������� ��������� VCPKG_ROOT
if(DEFINED ENV{VCPKG_ROOT})
    set(CMAKE_TOOLCHAIN_FILE "$ENV{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake"
        CACHE STRING "Vcpkg toolchain file")
else()
    message(FATAL_ERROR "Please define VCPKG_ROOT environment variable")
endif()

# ������� � ���������� ����� Crow ����� vcpkg
find_package(Crow CONFIG REQUIRED)

# ��������� ����������� ����
add_executable(CrowServer src/main.cpp)

# ������� ���������� Crow � ��������
target_link_libraries(CrowServer PRIVATE Crow::Crow)