# 🎮 Gyroscope Troubleshooting Guide - Minz Racing

## ❓ Gyroscope Not Working? Follow This Guide

### 🔍 **Step 1: Check if Your Device Supports Gyroscope**

#### Android (8.0+)
```
✅ Most modern Android phones have gyroscope
- Go to Settings > Apps > Permissions > Sensors
- Make sure the browser has sensor access
```

#### iOS (13.0+)
```
✅ Most iPhones have gyroscope
- Safari requires explicit permission (will pop up)
- Chrome: Settings > Site Settings > Device Motion
```

### 🧪 **Step 2: Test with Gyroscope Test Panel**

1. **Open `GYRO_TEST.html`** in your browser:
   ```
   https://your-domain/Minzv2/GYRO_TEST.html
   ```
   
2. **Click "Request Gyroscope Permission"** button
   - iOS: A popup will ask for permission
   - Android: Should activate immediately

3. **Watch the values update**:
   - `GAMMA` value should change when you tilt
   - `STEERING OUTPUT` bar should move left/right
   - Debug info shows real-time data

4. **Test the tilt**:
   - 🔴 **Tilt LEFT** → GAMMA becomes negative (e.g., -25.5°)
   - 🟢 **Tilt RIGHT** → GAMMA becomes positive (e.g., +28.2°)
   - ⭕ **Straight** → GAMMA near 0°

### 🎮 **Step 3: Verify in the Game**

1. **Open Minz Racing** in your browser
2. **Enter your name** and start the game
3. **Look at HUD** (top-left) - you should see:
   - `📱 GYRO: ON` = Gyroscope is enabled ✅
   - `📱 GYRO: OFF` = Gyroscope is disabled ❌
   - `📱 GYRO: DENIED` = Permission was denied ❌

4. **Test tilt during countdown** (3...2...1...GO!):
   - Tilt phone left → car should move left
   - Tilt phone right → car should move right

### 🐛 **Debug with Browser Console**

Open Developer Tools (F12) and check the Console tab:

#### ✅ Success Messages:
```
✅ Gyroscope enabled on Android
✅ Gyroscope enabled on iOS
```

#### ⚠️ Warning Messages:
```
⚠️ DeviceOrientation not supported on this device
❌ Gyroscope permission denied
Gyro - Alpha: 0.00, Beta: 5.23, Gamma: 25.50
Steering from gyro: 0.82
```

---

## 🔧 **Common Issues & Solutions**

### ❌ **Problem: "GYRO: OFF" appears in game**

**Cause**: Gyroscope permission wasn't requested or denied

**Solution**:
1. Close browser completely
2. Reopen and reload the game
3. Watch for permission popup (iOS)
4. Grant permission when asked

---

### ❌ **Problem: Console shows "DeviceOrientation not supported"**

**Cause**: Device or browser doesn't support gyroscope

**Solution**:
- ✅ Update to latest browser version (Chrome, Safari, Firefox)
- ✅ Try a different browser
- ✅ Use a real mobile device (emulators might not have gyro)
- ✅ Check device is NOT in airplane mode

---

### ❌ **Problem: Values are 0.00° in test panel**

**Cause**: Permission not granted or sensor not responding

**Solution**:
1. Click "Request Gyroscope Permission" again
2. Check iOS Settings > Safari > Preferences > Motion
3. Disable then re-enable in browser
4. Restart browser

---

### ❌ **Problem: Gamma doesn't change when I tilt**

**Cause**: 
- Phone orientation detection is wrong
- Screen rotation lock is ON
- Dead zone is too large

**Solution**:
1. Disable screen rotation lock (Settings > Display)
2. Rotate phone to landscape mode fully
3. Tilt more aggressively (>10°)
4. Try GYRO_TEST.html to verify values

---

### ❌ **Problem: Car moves in wrong direction**

**Cause**: Phone is held upside-down or sideways

**Solution**:
- Hold phone in **landscape mode** (home button on left or right)
- Tilt **left edge down** = car goes LEFT
- Tilt **right edge down** = car goes RIGHT

---

## 📱 **Device-Specific Settings**

### **iOS (iPhone/iPad)**
1. Open Settings > Safari
2. Scroll down to "Preferences"
3. Enable "Motion & Orientation"
4. Grant permission when game asks

### **Android (Chrome)**
1. Open Chrome > Settings > Site Settings
2. Find "Device Motion" or "Sensors"
3. Enable for the game's domain
4. Some phones: Settings > Apps > Permissions > Sensors

### **Samsung Internet**
1. Settings > Permissions > Sensors
2. Allow for the website

### **Firefox (Android)**
1. Settings > Permissions > Sensors
2. Enable

---

## 📊 **What the Numbers Mean**

| Value | Name | What It Does | Range |
|-------|------|-------------|-------|
| **ALPHA** | Z-axis (Rotation) | Used for compass | 0-360° |
| **BETA** | X-axis (Front/Back) | Tilt up/down | -180 to +180° |
| **GAMMA** | Y-axis (Left/Right) | 🎯 **USED FOR STEERING** | -90 to +90° |

### **GAMMA Explanation** (Most Important)
- **Negative**: Tilt phone LEFT
- **Positive**: Tilt phone RIGHT
- **0**: Phone is level/straight
- **Threshold**: ±8° (must tilt at least 8° to activate)
- **Max**: ±25° (maximum steering range)

### **Game Steering Output**
```
Steering Value = -1 (full left)
     ↓
     └─ Normalized from GAMMA
     ↑
Steering Value = 0 (straight)
     ↓
     └─ When GAMMA is between -8° and +8°
     ↑
Steering Value = +1 (full right)
```

---

## 🚀 **Testing Checklist**

- [ ] Device is in landscape orientation
- [ ] No screen rotation lock active
- [ ] Browser is up-to-date
- [ ] Gyroscope permission granted (check browser settings)
- [ ] Test panel shows gamma values changing with tilt
- [ ] HUD shows "📱 GYRO: ON"
- [ ] Console shows "✅ Gyroscope enabled"
- [ ] Car responds to tilt in countdown
- [ ] Left tilt = left movement ✓
- [ ] Right tilt = right movement ✓

---

## 📞 **Still Not Working?**

1. **Open GYRO_TEST.html** and take a screenshot of values
2. **Check browser console** (F12) for error messages
3. **Try another browser** (Chrome, Safari, Firefox)
4. **Restart your phone**
5. **Check device isn't in airplane mode**

Share the console output and test panel screenshot for better debugging!

---

## 🎮 **Using Both Controls**

### **Combined Input System:**
- **Tilt phone**: Smooth steering (gyroscope)
- **Tap buttons**: Instant steering + acceleration (touch)
- **Both work together**: Use tilt for curves, tap for emergency dodge

### **Recommended Play Style:**
1. Use **tilt** for natural steering while driving
2. Tap **ACCEL button** to accelerate
3. Tap **NITRO** when you have energy
4. Use **tilt + buttons** together for precise control

---

**Version**: 1.0  
**Last Updated**: November 12, 2025

Need help? Check the console logs (F12) and test with GYRO_TEST.html! 🚀
