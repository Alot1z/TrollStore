# TrollStore Enhanced

A powerful iOS application installer that bypasses Apple's restrictions, providing advanced capabilities for iOS 17.0 and above. This enhanced version includes new exploits, improved features, and extended functionality.

## Core Features & Capabilities

### 1. Advanced Installation System
- **Persistent App Installation**: Apps remain installed through reboots
- **Custom IPA Support**: Install any compatible IPA file
- **URL Installation**: Direct install via URL scheme
- **Bulk Installation**: Install multiple apps simultaneously

### 2. Enhanced Security Bypass
- **CoreTrust Bypass**: Utilizing multiple exploit chains
- **Certificate Validation**: Bypasses Apple's signature requirements
- **Entitlement Management**: Custom entitlement injection
- **Root Access**: Controlled root helper functionality

### 3. Exploit Chain Integration

#### Primary Exploit (CVE-2023-42824)
- Kernel Memory Manipulation
- Process Injection Capabilities
- Root Permission Escalation
- iOS 17.0-17.1.1 Support
- Advanced MACF Policy Bypass

#### Secondary Exploit (CVE-2023-41991)
- Alternative Exploitation Path
- Enhanced Stability
- iOS 17.0-17.2 Support
- Sandbox Escape Functionality
- Process Integrity Validation Bypass

### 4. Advanced Features

#### URL Scheme Support
```
apple-magnifier://install?url=<URL_to_IPA>
apple-magnifier://enable-jit?bundle-id=<Bundle_ID>
```

#### Persistence Helper System
- System App Integration
- Icon Cache Management
- Automatic Reregistration
- Persistence Through Updates

#### Root Helper Functionality
- Privileged Operations Support
- Custom Binary Execution
- System Level Modifications
- Protected Resource Access

## Installation Methods

### Method 1: Direct Installation
1. Download latest IPA from Releases
2. Open in TrollStore
3. Install and trust the app
4. Configure persistence helper

### Method 2: GitHub Actions Build
1. Fork the repository
2. Enable GitHub Actions
3. Build will automatically create IPA
4. Download from Actions artifacts

### Method 3: Command Line Installation
```bash
# Clone repository
git clone https://github.com/YourUsername/TrollStore.git

# Install dependencies
brew install ldid
brew install theos

# Build project
make package
```

## Advanced Configuration

### Entitlements Management
Available entitlements for customization:
```xml
<!-- Root Access -->
<key>com.apple.private.security.container-required</key>
<false/>

<!-- Sandbox Escape -->
<key>com.apple.private.security.no-sandbox</key>
<true/>

<!-- Platform Application -->
<key>platform-application</key>
<true/>

<!-- Root Helper -->
<key>com.apple.private.persona-mgmt</key>
<true/>
```

### Known Limitations
- No TF_PLATFORM support
- Cannot spawn launch daemons
- Limited process injection capabilities
- No CS_PLATFORMIZED support

## Advanced App Environment Features

### 1. Dynamic Environment Control
#### Real-Time Variable Management
- **Live Environment Editing**: Modify app environment variables without restart
- **Persistent Changes**: Environment changes survive app restarts
- **Variable Templates**: Pre-configured environment sets for common scenarios
- **Import/Export**: Share environment configurations between apps

#### System Integration
```bash
# Example environment configuration
DYLD_INSERT_LIBRARIES=/path/to/tweak.dylib
TROLLSTORE_APP_PATH=/var/containers/Bundle/Application/AppUUID
TROLLSTORE_APP_GROUP=group.com.example.app
```

### 2. Advanced App Modifications

#### Memory Management
- **Dynamic Memory Limits**: Adjust app memory constraints
- **Jetsam Priority Control**: Modify app termination priority
- **Virtual Memory Enhancement**: Extended virtual memory capabilities
```bash
# Memory configuration example
TROLLSTORE_MEMORY_LIMIT=8192        # 8GB RAM limit
TROLLSTORE_JETSAM_PRIORITY=1        # High priority (lower number = higher priority)
TROLLSTORE_VM_EXTENDED=1            # Enable extended virtual memory
```

#### Process Control
- **Background Execution**: Enhanced background task capabilities
- **CPU Priority Management**: Control CPU resource allocation
- **Thread Management**: Advanced thread control and limits
```bash
# Process control configuration
TROLLSTORE_BACKGROUND_MODE=unlimited
TROLLSTORE_CPU_PRIORITY=80          # 0-100 scale
TROLLSTORE_THREAD_LIMIT=64          # Maximum thread count
```

### 3. Enhanced Security Controls

#### App Sandbox Configuration
- **Custom Sandbox Rules**: Define custom sandbox permissions
- **File System Access**: Extended file system access control
- **Network Security**: Custom network security rules
```xml
<!-- Advanced sandbox configuration -->
<key>com.apple.private.security.sandbox.override</key>
<dict>
    <key>file-access</key>
    <array>
        <string>/private/var/mobile/</string>
        <string>/var/mobile/Media/</string>
    </array>
    <key>network-access</key>
    <true/>
</dict>
```

#### Permission Management
- **Dynamic Permission Control**: Modify app permissions on-the-fly
- **Extended Capabilities**: Enable additional system capabilities
- **Privacy Settings**: Fine-grained privacy control
```bash
# Permission configuration
TROLLSTORE_CAMERA_ACCESS=1
TROLLSTORE_LOCATION_ALWAYS=1
TROLLSTORE_CONTACTS_ACCESS=1
```

### 4. Development Tools

#### Debug Environment
- **Advanced Logging**: Comprehensive logging system
- **Performance Monitoring**: Real-time performance metrics
- **Crash Analytics**: Enhanced crash reporting
```bash
# Debug configuration
TROLLSTORE_DEBUG_LEVEL=verbose
TROLLSTORE_PERFORMANCE_METRICS=1
TROLLSTORE_CRASH_REPORTS=/var/mobile/Logs/
```

#### Testing Features
- **Network Simulation**: Simulate different network conditions
- **Locale Testing**: Test app with different locales
- **Resource Limitations**: Simulate resource constraints
```bash
# Testing configuration
TROLLSTORE_NETWORK_CONDITION=3g
TROLLSTORE_TEST_LOCALE=en_US
TROLLSTORE_RESOURCE_LIMIT_MODE=1
```

### 5. App Enhancement Features

#### Performance Optimization
- **JIT Compilation**: Enhanced JIT support for better performance
- **Graphics Acceleration**: Advanced graphics capabilities
- **Cache Management**: Intelligent cache control
```bash
# Performance configuration
TROLLSTORE_JIT_ENABLED=1
TROLLSTORE_GPU_PERFORMANCE=high
TROLLSTORE_CACHE_SIZE=512MB
```

#### System Integration
- **Deep System Access**: Enhanced system API access
- **Inter-App Communication**: Advanced app communication features
- **System Service Integration**: Direct system service access
```bash
# System integration configuration
TROLLSTORE_SYSTEM_INTEGRATION=1
TROLLSTORE_IPC_ENABLED=1
TROLLSTORE_SYSTEM_SERVICES=1
```

### Using Environment Features

1. **Basic Usage**
```bash
# Open TrollStore
# Select target app
# Go to "Environment" tab
# Add or modify variables
```

2. **Template Usage**
```bash
# Select "Templates" in Environment tab
# Choose template type:
# - Development
# - Production
# - Testing
# Apply template
```

3. **Advanced Configuration**
```bash
# Access "Advanced Settings"
# Enable required features
# Configure specific parameters
# Apply and restart app
```

## Debugging & Troubleshooting

### Debug Logging
Enable advanced logging in Settings:
1. Open TrollStore
2. Go to Settings > Advanced
3. Enable Debug Logging
4. View logs in /var/log/trollstore.log

### Common Issues
1. **Installation Fails**
   - Verify iOS version compatibility
   - Check available storage
   - Ensure network connectivity

2. **Apps Crash on Launch**
   - Verify entitlements configuration
   - Check for banned entitlements
   - Validate binary signatures

3. **Persistence Issues**
   - Reinstall persistence helper
   - Verify system app status
   - Check icon cache status

## Security Considerations
- All operations are sandboxed by default
- Root access is controlled and limited
- System integrity is maintained
- No permanent system modifications

## Build Configuration

### Requirements
- macOS/Linux build system
- Theos installed
- iOS SDK 16.2+
- ldid utility
- libarchive

### Build Process
```bash
# Set environment
export THEOS=/opt/theos
export SDKVERSION=16.2
export SYSROOT=/opt/theos/sdks/iPhoneOS16.2.sdk

# Build package
make package FINALPACKAGE=1
```

## Credits & Acknowledgments
- Original TrollStore by [@opa334](https://twitter.com/opa334)
- CoreTrust bug by [@alfiecg_dev](https://twitter.com/alfiecg_dev)
- Google TAG - Original vulnerability discovery
- [@LinusHenze](https://twitter.com/LinusHenze) - installd bypass

## Version History
- 2.0.0: Initial iOS 17 support
- 2.0.1: Added CVE-2023-42824
- 2.0.2: Integrated CVE-2023-41991
- 2.0.3: Enhanced persistence system

## License
This project is licensed under the same terms as the original TrollStore.

## Support & Community
- [GitHub Issues](https://github.com/YourUsername/TrollStore/issues)
- [Discord Server](https://discord.gg/YourServer)
- [Reddit Community](https://reddit.com/r/TrollStore)
