# Twilight 1.9.2 Hotfix November 04, 2024
1. Fixed Cr3 BSOD
2. Fixed Esp / Skeleton Posation
3. Fixed Recoil
4. All the functions now supporting TwGetFunctionSpoofedEx
```cpp
   TwGetFunctionSpoofedEx(void* Function, bool Function)
```

## New Recoil System (Soon Will be adjustable)

### Old recoil method
```cpp
TwWrite<float>(lEntity.GetAngle + Get->o_HorizontalRecoil, 0);
TwWrite<float>(lEntity.GetAngle + Get->o_VerticalRecoil, 0);
```

### New Recoil Method
```cpp
TwWrite<float>(lEntity.GetAngle + Get->o_HorizontalRecoil, 0);
TwWrite<float>(lEntity.GetAngle + Get->o_Recoil, 1);
TwWrite<float>(lEntity.GetAngle + Get->o_RecoilC, 0);
```
### Twilight Public launcher
1. Updated to latest endpoint
2. Battleye Apc bypass
3. EAAC Bypass

- _Please note before we luanch any update or bypass we have test our products first so 2 & 3 will take a time to be released we want to make sure it's safe 100%_


### Twilight Lua API
The Twilight Lua API is a feature we’ve been developing over the past few months. This addition allows users not only to customize settings through the Twilight GUI but also to modify the aimbot, ESP, and nearly all Twilight features. We’re continuing to refine this functionality to enhance both our product and user experience. We encourage you to explore how our Lua API works, and we’d love to hear feedback from the community to improve and tailor the API to meet user needs.

### Q & A 
#### When will it be released 
_There’s no specific release date yet, but we look forward to hearing from our community._

#### Is this feature included in the Twilight Subscription
_Yes, it’s included. However, we’re considering the possibility of offering a dedicated subscription option for developers._

#### Will it be free
_Yes, it’s completely free. However, we plan to create a marketplace to help users avoid scams from those selling fake scripts._
| Var | Type | Description |
| ------------- | ------------- | ------------- |
| b_TriggerBot   | BOOLEAN  | Enables or disables the trigger bot  |
| b_Trigger_Key   | INTEGER  | The key assigned for activating the trigger bot  |

#### Twilight C++ Function 
```cpp
void TwTriggerBot(bool enabled);
void TwTriggerKey(int key)
```
#### Adjusting BOOLEAN & INTEGER 
```lua
TwSetTriggerBot(true)
TwSetTriggerKey(0x02)
```
_You can find all keyboard and mouse virtual keys [here](https://learn.microsoft.com/en-us/windows/win32/inputdev/virtual-key-codes)._

#### Vector3 
| Var  | Type | Description |
| ------------- | ------------- | ------------- |
| v1  | Vector3  | The first vector instance for operations  |
| v2  | Vector3  | The second vector instance for operations  |
| ResultAdd  | Vector3  | Result of adding two vectors  |
| ResultSub  | Vector3  | Result of subtracting two vectors  |
| ResultScale  | Vector3  | Result of scaling a vector by a float  |
| Distance  | float  | Distance between two vectors  |

#### Twilight C++ Functions 
```cpp
Vector3 TwVector3(float x, float y, float z);
Vector3 operator+(const Vector3& V);
Vector3 operator-(const Vector3& V);
Vector3 operator*(float Scale) const;
float TwDistance(const Vector3& GetDistance) const; 
```
### Using Twilight LUA API
```lua
-- Create two vectors
local v1 = Vector3(1.0, 2.0, 3.0)
local v2 = Vector3(4.0, 5.0, 6.0)

-- Calculate the distance between the two vectors
local Distance = v1:TwDistance(v2)
```

### Example of calculating the local angle 
```lua
local lPlayer = Vector3(lEntity.lPlayer.X, lEntity.lPlayer.Y, lEntity.lPlayer.Z)  -- Local player position
local m_lEntity = Vector3(m_lEntity.X, m_lEntity.Y, m_lEntity.Z)                  -- Target enemy position

local Disctance = lPlayer:TwDistance(m_lEntity)  -- Calculate distance to the enemy


local EnemyPosition = (m_lEntity - lPlayer):Normalized() -- Scaling the direction vector

local TrackingSpeed = 5.0  -- Speed to move towards the enemy
local CalculatedAngle = lPlayer + (EnemyPosition * TrackingSpeed)  -- Calculated position the enemy

if Disctance < 100.0 then
    -- Trigger VK_RBUTTON
    SetKey(0x2) 
end
```

### Known Issues for 1.9.2
NONE


