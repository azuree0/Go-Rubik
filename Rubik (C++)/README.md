## Directory structure

Rubik (C++)/

├── main.cpp          # Main application and SFML GUI

├── rubik_cube.h/cpp  # Rubik's cube logic and rotation mechanics

├── renderer.h/cpp    # 3D OpenGL rendering system

├── CMakeLists.txt    # Build configuration

├── .gitignore        # Git ignore file

└── README.md         # This file

### Prerequisites

- CMake 3.15 or later
- C++17 compatible compiler
- SFML 2.5 or later
- OpenGL support

### Windows Build Instructions

1. Install SFML:
   - Download from https://www.sfml-dev.org/download.php
   - Extract to a location (e.g., `C:/SFML`)

2. Configure and build:
   ```bash
   mkdir build
   cd build
   cmake .. -DSFML_ROOT=C:/SFML
   cmake --build . --config Release
   ```

3. Copy SFML DLLs (if not already done):
   ```powershell
   Copy-Item C:\SFML\bin\sfml-*.dll build\Release\
   ```

4. Run:
   ```bash
   cd build\Release
   .\RubikGame.exe
   ```
   Or from the project root:
   ```bash
   .\build\Release\RubikGame.exe
   ```

### Alternative: Using vcpkg

If you have vcpkg installed:
```bash
vcpkg install sfml
cmake .. -DCMAKE_TOOLCHAIN_FILE=[vcpkg root]/scripts/buildsystems/vcpkg.cmake
cmake --build . --config Release
```

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
