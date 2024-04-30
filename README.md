Вы продолжаете проходить стажировку в "Formatter Inc." (см подробности).

В прошлый раз ваше задание заключалось в настройке автоматизированной системы CMake.

Сейчас вам требуется настроить систему непрерывной интеграции для библиотек и приложений, с которыми вы работали в прошлый раз. Настройте сборочные процедуры на различных платформах:

сборка на операционной системе Linux с использованием компиляторов gcc и clang;
сборка на операционной системе Windows

Сборка на Linux (Ubuntu)

name: CMake_Build

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]


  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
  
    
    steps:
    - name: checkout
      uses: actions/checkout@v3
    
    - name: Build a formatter library gcc
      run: |
        cmake -H. -B_build -DCMAKE_C_COMPILER=gcc
        cmake --build _build
      shell: bash
      working-directory: formatter_lib
      
    - name: Build a formatter_ex library clang
      run: |
        cmake -H. -B_build -DCMAKE_C_COMPILER=clang
        cmake --build _build
      shell: bash
      working-directory: formatter_ex_lib
      
    - name: Build a hello_world application gcc
      run: |
        cmake -H. -B_build -DCMAKE_C_COMPILER=gcc
        cmake --build _build
      shell: bash
      working-directory: hello_world_application
      
    - name: Build a solver application clang
      run: |
        cmake -H. -B_build -DCMAKE_C_COMPILER=clang
        cmake --build _build
      shell: bash
      working-directory: solver_application

Сборка на windows


name: CMake_Build

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]


  workflow_dispatch:

jobs:
  build:
    runs-on: windows-latest
  
    
    steps:
    - name: checkout
      uses: actions/checkout@v3
    
    - name: Build a formatter library gcc
      run: |
        cmake -H. -B_build -DCMAKE_C_COMPILER=gcc
        cmake --build _build
      shell: bash
      working-directory: formatter_lib
      
    - name: Build a formatter_ex library clang
      run: |
        cmake -H. -B_build -DCMAKE_C_COMPILER=clang
        cmake --build _build
      shell: bash
      working-directory: formatter_ex_lib
      
    - name: Build a hello_world application gcc
      run: |
        cmake -H. -B_build -DCMAKE_C_COMPILER=gcc
        cmake --build _build
      shell: bash
      working-directory: hello_world_application
      
    - name: Build a solver application clang
      run: |
        cmake -H. -B_build -DCMAKE_C_COMPILER=clang
        cmake --build _build
      shell: bash
      working-directory: solver_application
