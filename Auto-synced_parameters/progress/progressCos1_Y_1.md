# progressCos1_Y_1  
and alternative code **[progressCos1_Yb_1](#progresscos1_yb_1)**  

---

### progressCos1_Y_1 

![](images/progressCos1_Y_1.png)  
### Three-point progress: 1 ...  adjustable central value  ... 1  
  
  ---
    
### Required global definitions and declarations:
*(add outside and above all shaders and functions):*
```` Code
//--------------------------------------------------------------//
// Definitions, declarations und macros
//--------------------------------------------------------------//

#define TWO_PI  6.2831853072
float _Progress;
````

---
  
### Code (Example as a function):  
```` Code
float fn_progressCos1_Y_1 (float centralValue)
{
   float progressCos1_0_1 = cos(_Progress * TWO_PI) * 0.5 + 0.5;
   return progressCos1_0_1 * (1.0 - centralValue) + centralValue;
}
````
Detais: [Documentation of the variable `progressCos1_0_1`](progressCos1_0_1.md)  
 
---
  
### Parameter Description:
  
1. `_Progress`
   Auto-synced parameter
   - **Type:** `float`, global  
   - **Value range:** 0.0 to 1.0
   - Detais: [Documentation of the variable `_Progress`](_Progress.md) 
     
2. **TWO_PI**: Defines the wavelength as one complete wave.  
   Higher values shorten the wavelength (more waves per effect runtime)  
   
3. `* 0.5` Scales the cos return values (+1 .. -1 ... +1) to +0.5 .. -0.5 .. +0.5  

4. `+ 0.5` Moves the wave in the positive range: +1 .. 0 .. +1
     
5. `centralValue`:  
   The adjustable central value.  
   This defines the return value at 50% effect progress  (`_Progress = 0.5`).  
    see also ["Return value"](#return-value)
   - **Type:** `float`, local   
   - **Permissible value range:** Unlimited, positive and negative. 
  
---
  
## Return value:
   - If `_Progress == 0.0` then 1.0  
   - If `_Progress == 0.5`then identical to `centralValue` (unlimited, positive and negative)  
      Other control behavior see the alternative code `progressCos1_Yb_1` below.
   - If `_Progress == 1.0` then 1.0  
   - The return values between the three Progress points (0.0 and 0.5 and 1.0) are calculated by the cosine wave.
   - **Type:** `float`   
   - **Value range:** Unlimited, positive and negative.  

---
---

## Alternatives:

### Local code in the shader instead of the function:  
If you need a settable and in addition a fixed progress curve in a single shader, then one of these variants could be useful:

#### Two progress curves available `progressCos1_0_1` and `progressCos1_Y_1`:
```` Code
float progressCos1_0_1 = cos(_Progress * TWO_PI) * 0.5 + 0.5;
float progressCos1_Y_1 = progressCos1_0_1 * (1.0 - centralValue) + centralValue;
````
  
  or
  
#### Two progress curves available `progressCos0_1_0` and `progressCos1_Y_1`:

```` Code
   float progressCos0_1_0 = cos(_Progress * TWO_PI) *-0.5 + 0.5;
   float progressCos1_Y_1 = 1.0 - progressCos0_1_0 * (1.0 - centralValue);
````

or  
  
  
#### If only one variable is needed:
```` Code
float progressCos1_Y_1 = 1.0 
                       - (cos(_Progress * TWO_PI) *-0.5 + 0.5)
                       * (1.0 - centralValue);
````
  
  
---
---
---



## progressCos1_Yb_1
#### Alternative (inverse) control behavior of parameter `centralValue`:

```` Code
   float progressCos0_1_0 = cos(_Progress * TWO_PI) *-0.5 + 0.5;
   float progressCos1_Yb_1 = 1.0 - progressCos0_1_0 * centralValue;
````

#### Return value of `progressCos1_Yb_1` (deviating from `progressCos1_Y_1`):
   - If `_Progress == 0.0` then 1.0  
   - If `_Progress == 0.5` and   
      - If `centralValue` < 0.0  then return values > 1  
      - If `centralValue` == 0.0 then 1.0  
      - If `centralValue` == 0.5 then 0.5 
      - If `centralValue` == 1.0 then 0.0  
      - If `centralValue` > 1.0  then negative return values  
   - If `_Progress == 1.0` then 1.0  
   - The return values between the three Progress points (0.0 and 0.5 and 1.0) are calculated by the cosine wave.
   - **Type:** `float`   
   - **Value range:** Unlimited, positive and negative.  
