##  Directory structure

Go (C++)/

├── main.cpp          # Main application and SFML GUI

├── board.h/cpp       # Board logic and Go rules

├── game.h/cpp        # Game state management

├── CMakeLists.txt    # Build configuration

├── .gitignore        # Git ignore file

└── README.md         # This file

## Prerequisites

Before building, ensure you have:

- **C++ Compiler** with C++17 support:
  - Windows: Visual Studio 2019 or later, or MinGW-w64
  - Linux: GCC 7+ or Clang 5+
  - macOS: Xcode 10+ or Clang 5+

- **CMake** 3.15 or later
  - Download from [cmake.org](https://cmake.org/download/)

- **SFML 2.5** or later
  - **Windows**: Download from [sfml-dev.org](https://www.sfml-dev.org/download.php)
    - Extract to a location (e.g., `C:\SFML`)
    - Set `SFML_ROOT` environment variable or specify in CMake
  - **Linux**: Install via package manager
    ```bash
    # Ubuntu/Debian
    sudo apt-get install libsfml-dev
    
    # Fedora
    sudo dnf install SFML-devel
    ```
  - **macOS**: Install via Homebrew
    ```bash
    brew install sfml
    ```

## Building the Project

### Windows

**Using Visual Studio (Recommended)**:
```powershell
mkdir build
cd build
cmake .. -DSFML_ROOT=C:/SFML       # Adjust path to your SFML installation
cmake --build . --config Release
```

**Using MinGW**:
```powershell
mkdir build
cd build
cmake .. -G "MinGW Makefiles" -DSFML_ROOT=C:/SFML
cmake --build .
```

### Linux/Mac

```bash
mkdir build
cd build
cmake ..
make -j4
```

**Note:** The first build may take several minutes as it downloads and compiles dependencies.

## Running the Game

After building, run the executable:

- **Windows**: `build/Release/GoGame.exe` or `build/Debug/GoGame.exe`

- **Linux/macOS**: `./build/GoGame`

## Troubleshooting

### CMake can't find SFML
- Set the `SFML_ROOT` environment variable to your SFML installation directory
- Or specify it during CMake configuration: `cmake .. -DSFML_ROOT=/path/to/sfml`

### Build fails
- Ensure you have C++17 support enabled: Check your compiler version
- Check that SFML is properly installed and linked
- Verify CMake version is 3.15 or later: `cmake --version`
- On Windows, make sure Visual Studio Build Tools or MinGW is installed

### Font not loading
- The game tries to load Arial or Calibri from Windows fonts directory
- On Linux/macOS, you may need to adjust the font path in `main.cpp`
- The game will still work without fonts, but text may not display

### Game doesn't respond to clicks
- Check that the executable is running properly
- Ensure SFML libraries are in the same directory as the executable (Windows) or in system library path (Linux/macOS)


