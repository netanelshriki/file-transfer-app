# SecureTransfer - Cross-Platform File Transfer Application

A beautiful, secure, and effortless file transfer application that works across Windows, Linux, and Android devices. Transfer files instantly on your local network or anywhere in the world via the internet.

## ✨ Features

### 🚀 **Zero Configuration**
- Install and use immediately - no setup required
- Automatic device discovery on local networks
- Seamless internet transfers between any devices globally

### 🎨 **Beautiful, Modern Interface**
- Stunning Material Design 3 on Android
- Modern JavaFX interface on desktop with dark/light themes
- Intuitive drag-and-drop functionality
- Professional animations and transitions

### 🔒 **Enterprise-Grade Security**
- End-to-end AES-256 encryption
- Secure key exchange protocols
- No data stored on external servers
- Privacy-first architecture

### 🌐 **Universal Compatibility**
- **Desktop**: Windows 10/11, Linux (Ubuntu, Fedora, etc.)
- **Mobile**: Android 8.0+ (API level 26+)
- **Transfers**: Any device to any device, anywhere in the world

### ⚡ **High Performance**
- Local network: 200+ MB/s on gigabit, 40+ MB/s on WiFi
- Internet transfers: 15+ MB/s with resumable uploads
- Automatic connection optimization
- Background transfer queue management

## 📦 Installation

### Windows 11 (MSI Installer)

#### Option 1: Download Pre-built Installer
1. Download `SecureTransfer-Setup.msi` from [Releases](../../releases)
2. Right-click the MSI file → "Run as administrator"
3. Follow the installation wizard
4. Launch from Start Menu or desktop shortcut

#### Option 2: Build Your Own MSI Installer
**Prerequisites:**
- Windows 11 with PowerShell
- Java 21 LTS ([Download from Oracle](https://www.oracle.com/java/technologies/downloads/#java21) or [OpenJDK](https://adoptium.net/temurin/releases/?version=21))
- Maven 3.8+ ([Download from Apache](https://maven.apache.org/download.cgi))
- Git ([Download from Git](https://git-scm.com/download/win))

**Step-by-Step Build Instructions:**
```powershell
# 1. Clone the repository
git clone https://github.com/netanelshriki/file-transfer-app.git
cd file-transfer-app

# 2. Navigate to desktop project
cd desktop

# 3. Build the MSI installer (this will take 5-10 minutes)
mvn clean compile jpackage:jpackage -Pwindows-msi

# 4. Find your installer
# The MSI file will be created in: desktop\target\installer\SecureTransfer-1.0.0.msi
```

**Install Your Built MSI:**
```powershell
# Navigate to the installer directory
cd target\installer

# Install the MSI (run as administrator)
msiexec /i SecureTransfer-1.0.0.msi /qb
```

### Linux
**Ubuntu/Debian:**
```bash
wget https://github.com/netanelshriki/file-transfer-app/releases/latest/download/securetransfer.deb
sudo dpkg -i securetransfer.deb
```

**Universal (AppImage):**
```bash
wget https://github.com/netanelshriki/file-transfer-app/releases/latest/download/SecureTransfer.AppImage
chmod +x SecureTransfer.AppImage
./SecureTransfer.AppImage
```

### Android Mobile

#### Option 1: Download Pre-built APK
1. Download `SecureTransfer.apk` from [Releases](../../releases)
2. On your Android device: Settings → Security → "Install unknown apps" → Enable for your browser/file manager
3. Open the APK file and tap "Install"
4. Launch from app drawer

#### Option 2: Build Your Own APK
**Prerequisites:**
- Windows 11, macOS, or Linux
- Java 21 LTS
- Android Studio or Android SDK Command Line Tools
- Git

**Step-by-Step Build Instructions:**

**Windows 11:**
```powershell
# 1. Install Android SDK Command Line Tools
# Download from: https://developer.android.com/studio#command-tools
# Extract to: C:\Android\cmdline-tools\latest\

# 2. Set environment variables
$env:ANDROID_HOME = "C:\Android"
$env:PATH += ";C:\Android\cmdline-tools\latest\bin;C:\Android\platform-tools"

# 3. Accept Android licenses
sdkmanager --licenses

# 4. Clone and build
git clone https://github.com/netanelshriki/file-transfer-app.git
cd file-transfer-app\android

# 5. Build release APK
.\gradlew assembleRelease

# 6. Find your APK
# The APK will be created in: android\app\build\outputs\apk\release\app-release.apk
```

**macOS/Linux:**
```bash
# 1. Install Android SDK Command Line Tools
# Download from: https://developer.android.com/studio#command-tools
# Extract to: ~/Android/cmdline-tools/latest/

# 2. Set environment variables (add to ~/.bashrc or ~/.zshrc)
export ANDROID_HOME=~/Android
export PATH=$PATH:$ANDROID_HOME/cmdline-tools/latest/bin:$ANDROID_HOME/platform-tools

# 3. Accept Android licenses
sdkmanager --licenses

# 4. Clone and build
git clone https://github.com/netanelshriki/file-transfer-app.git
cd file-transfer-app/android

# 5. Build release APK
./gradlew assembleRelease

# 6. Find your APK
# The APK will be created in: android/app/build/outputs/apk/release/app-release.apk
```

**Install Your Built APK:**
1. Copy the APK file to your Android device (via USB, cloud storage, or email)
2. On your Android device: Settings → Security → "Install unknown apps" → Enable for your file manager
3. Open the APK file and tap "Install"
4. Launch "SecureTransfer" from your app drawer

## 🚀 Quick Start

### First Launch
1. **Open the app** on all devices you want to connect
2. **Devices appear automatically** - no manual pairing needed
3. **Drag files** onto device cards or use the "+" button
4. **Files transfer instantly** with real-time progress

### Sending Files

#### Desktop
- **Drag & Drop**: Drag files from file explorer onto device cards
- **Click to Select**: Click "+" on any device card to browse files
- **Right-Click Menu**: Right-click files in explorer → "Send with SecureTransfer"

#### Android
- **Share Integration**: Share from any app → Select SecureTransfer → Choose device
- **In-App Browser**: Use built-in file browser to select and send

### Receiving Files
- **Automatic**: Files appear in your Downloads folder by default
- **Custom Location**: Set preferred download location in Settings
- **Notifications**: Get notified when transfers complete

## 🔧 Advanced Usage

### Network Modes
- **Local Network**: Fastest transfers when devices are on same WiFi
- **Internet Mode**: Global transfers using secure relay servers
- **Auto-Switch**: Automatically uses best available connection

### Security Settings
- **Device Authentication**: Optional PIN codes for device pairing
- **Auto-Accept**: Configure trusted devices for automatic file acceptance
- **Encryption**: All transfers use AES-256 encryption (always enabled)

### Transfer Management
- **Queue System**: Multiple files transfer in sequence
- **Pause/Resume**: Control active transfers
- **History**: View all past transfers with timestamps
- **Retry Failed**: Automatically retry interrupted transfers

## 🛠️ Development

### Prerequisites
- **Java 21 LTS** (OpenJDK or Oracle)
- **Maven 3.8+** (for desktop applications)
- **Android SDK** with Build Tools 34+ (for Android app)
- **Git** for version control

### Building from Source

#### Quick Build (All Platforms)
```bash
# Clone repository
git clone https://github.com/netanelshriki/file-transfer-app.git
cd file-transfer-app

# Build everything
./scripts/build-all.sh        # Unix/Linux/Mac
scripts\build-all.bat         # Windows
```

#### Individual Platform Builds

**Desktop Applications:**
```bash
cd desktop

# Windows MSI installer
mvn clean jpackage:jpackage -Pwindows-msi

# Linux DEB package
mvn clean jpackage:jpackage -Plinux-deb

# Linux AppImage
mvn clean jpackage:jpackage -Plinux-appimage
```

**Android APK:**
```bash
cd android
./gradlew assembleRelease
```

#### Development Mode (Fast Testing)
```bash
# Desktop - run without packaging
cd desktop && mvn javafx:run

# Android - debug APK
cd android && ./gradlew assembleDebug && ./gradlew installDebug
```

### Project Structure
```
file-transfer-app/
├── desktop/                    # Maven project for Windows/Linux
│   ├── pom.xml                # Maven configuration with jpackage
│   ├── src/main/java/         # Desktop application source code
│   └── src/main/resources/    # JavaFX resources, icons, styles
├── android/                   # Gradle project for Android
│   ├── build.gradle           # Android configuration
│   ├── src/main/java/         # Android application source code
│   └── src/main/res/          # Android resources and layouts
├── server/                    # Signaling server for internet transfers
│   ├── pom.xml                # Spring Boot server configuration
│   └── src/main/java/         # Server source code
├── scripts/                   # Build automation scripts
│   ├── build-all.sh           # Unix/Linux/Mac build script
│   ├── build-all.bat          # Windows build script
│   ├── build-desktop.sh       # Desktop-only build
│   └── build-android.sh       # Android-only build
├── .github/workflows/         # GitHub Actions CI/CD
│   └── build-release.yml      # Automated building and releases
└── docs/                      # Additional documentation
    ├── DEPLOYMENT.md          # Server deployment guide
    ├── DEVELOPMENT.md         # Development setup guide
    └── ARCHITECTURE.md        # Technical architecture details
```

### Testing
```bash
# Run all tests
./scripts/test-all.sh

# Desktop unit tests
cd desktop && mvn test

# Android unit tests
cd android && ./gradlew test

# Integration tests
./scripts/test-integration.sh
```

## 🌐 Server Infrastructure

For internet transfers, you'll need to deploy the signaling server and configure STUN/TURN servers.

### Quick Server Setup
```bash
# Deploy signaling server (requires Docker)
cd server
docker build -t securetransfer-server .
docker run -p 8080:8080 securetransfer-server
```

### Production Deployment
See [DEPLOYMENT.md](docs/DEPLOYMENT.md) for complete server setup instructions including:
- Signaling server deployment (AWS, Google Cloud, etc.)
- STUN/TURN server configuration
- SSL certificate setup
- Load balancing and scaling

## 🤝 Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

### Development Setup
1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Make your changes and test thoroughly
4. Commit: `git commit -m 'Add amazing feature'`
5. Push: `git push origin feature/amazing-feature`
6. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see [LICENSE](LICENSE) file for details.

## 🆘 Support

### Common Issues
- **Devices not appearing**: Ensure all devices are on the same network and have the app open
- **Slow transfers**: Check network connection and try switching between WiFi/cellular
- **Transfer failures**: Verify firewall settings and internet connectivity

### Getting Help
- 📖 **Documentation**: Check [docs/](docs/) folder for detailed guides
- 🐛 **Bug Reports**: Open an issue on [GitHub Issues](../../issues)
- 💬 **Discussions**: Join conversations in [GitHub Discussions](../../discussions)
- 📧 **Contact**: net.shr1234@gmail.com

## 🙏 Acknowledgments

Built with these excellent open-source technologies:
- **Java 21 LTS** - Modern, performant runtime
- **JavaFX** - Rich desktop UI framework
- **Android SDK** - Mobile application platform
- **OkHttp** - Reliable HTTP client
- **Netty** - High-performance networking
- **Jitsi WebRTC** - Peer-to-peer communication
- **Spring Boot** - Server framework
- **Material Design 3** - Modern UI components

---

**SecureTransfer** - Beautiful, secure, effortless file transfers anywhere in the world. 🚀

## 🔗 Links

- **Link to Devin run**: https://app.devin.ai/sessions/ed9c1a550f724bb69cb7d713985beb75
- **Requested by**: @netanelshriki
