# Windows

Instructions for building this project on Windows.

## 1. Prerequisites

The following tools must be installed manually:

- [Visual Studio 2022](https://visualstudio.microsoft.com/vs/)
  - Workload: Desktop development with C++

- [Git for Windows](https://git-scm.com/)
  - Install Git if not already installed, and the related commands depend on **Git Bash's 3rd-party binaries** 
  - during installation, you need to select either **"Git from the command line and also from 3rd-party software"** or **"Use Git and optional Unix tools from the Command Prompt"**


## 2. Clone the Repository

```bash
# Clone the repository
git clone --recurse-submodules https://github.com/k4yt3x/video2x.git
cd video2x
```

## 3. Install Dependencies

```bash
# Versions of manually installed dependencies
ffmpegVersion="7.1"
ncnnVersion="20241226"

# Download and extract FFmpeg
curl -Lo ffmpeg-shared.zip "https://github.com/GyanD/codexffmpeg/releases/download/$ffmpegVersion/ffmpeg-$ffmpegVersion-full_build-shared.zip"
unzip ffmpeg-shared.zip -d third_party
mv "third_party/ffmpeg-$ffmpegVersion-full_build-shared" "third_party/ffmpeg-shared"
rm ffmpeg-shared.zip

# Download and extract ncnn
curl -Lo ncnn-shared.zip "https://github.com/Tencent/ncnn/releases/download/$ncnnVersion/ncnn-$ncnnVersion-windows-vs2022-shared.zip"
unzip ncnn-shared.zip -d third_party
mv "third_party/ncnn-$ncnnVersion-windows-vs2022-shared" "third_party/ncnn-shared"
rm ffmpeg-shared.zip
```

## 4. Build the Project

1. Open Visual Studio, select the **CMakeLists.txt** file in the **Video2x** project within **Solution Explorer**, right-click, and choose **CMake Settings**.
1. If everything goes smoothly, the steps above should generate the **CMakeSettings.json** file. Open the generated **CMakeSettings.json** file and enter the following in the **Command arguments** field:  
`-DVIDEO2X_USE_EXTERNAL_NCNN=OFF -DVIDEO2X_USE_EXTERNAL_SPDLOG=OFF -DVIDEO2X_USE_EXTERNAL_BOOST=OFF`
1. Right-click on the **Video2x** project in **Solution Explorer** and select **Switch to CMake Targets View**.
1. The built binaries will be located in `video2x\out\build`.
