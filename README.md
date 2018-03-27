# SteamVR-without-an-HMD

SteamVR Tracking without an HMD

Reference.
1. http://help.triadsemi.com/steamvr-tracking/steamvr-tracking-without-an-hmd
2. http://www.pencilsquaregames.com/getting-steamvr-tracking-data-in-unity-without-a-hmd/

------------------------------------------------------------
  
StreanVR (WIN 10) - OpenVR  
Step 1: 路徑 C:\Program Files (x86)\Steam\logs\vrserver.txt  
找出 vrsettings 位置  

```
[Settings] ... C:\Program..\Steam\steamapps\common\SteamVR\resources\settings\default.vrsettings  
[Settings] ... C:\Program..\Steam\steamapps\common\SteamVR\drivers\htc\resources\settings\default.vrsettings  
[Settings] ... C:\Program..\Steam\steamapps\common\SteamVR\drivers\lighthouse\resources\settings\default.vrsettings  
[Settings] ... C:\Program..\Steam\steamapps\common\SteamVR\drivers\null\resources\settings\default.vrsettings  
[Settings] ... C:\Program..\Steam\config\steamvr.vrsettings  
```

Step2: 修改 resources\settings\default.vrsetting  
將內容修改成  

```
"requireHmd" : false  
"forcedDriver" : "null"  
"activateMultipleDrivers" : true  
```

Step3: 修改 null\resources\settings\default.vrsettings  
將內容修改成  

```
{
	"driver_null" : {
		"enable" : true,
		"serialNumber" : "Null Serial Number", 
		"modelNumber" : "Null Model Number",
		"windowX" : 0,
		"windowY" : 0,
		"windowWidth" : 2160,
		"windowHeight" : 1200,
		"renderWidth" : 1512,
		"renderHeight" : 1680,
		"secondsFromVsyncToPhotons" : 0.01111111,
		"displayFrequency" : 90.0
	}
}
```



完成後 SteamVR圖示會變更.  

Step4: Unity OpenVR 調整  
開啟 Unity, 將 SteamVR Camera 的Target eye 改為 none,  
[CameraRig] 的 Left, Right, 改為 Tracker1, Tracker2  
Tracker1, Tracker2 的 index 改為 1 跟 2.   
  
VIVE 頭盔 跟 手把 兩個皆可不使用.  
只使用Tracker.  
