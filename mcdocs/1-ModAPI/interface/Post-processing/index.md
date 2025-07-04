--- 
sidebarDepth: 1 
--- 
# Index 

--- 

- [Vignette](#Vignette) 
- [Blur](#Blur) 
- [Color](#Color) 
- [Lens Effect](#Lens Effect) 

### Vignette 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CheckVignetteEnabled](Vignette.md#checkvignetteenabled) | <span style="display:inline;color:#7575f9">Client</span> | Check whether the screen vignetting effect is enabled. | 
| [SetEnableVignette](色彩.md#setenablevignette) | <span style="display:inline;color:#7575f9">客户端</span> | Set whether to enable the screen vignetting effect. When enabled, vignetting will appear around the player's screen. The effect parameters can be set through other Vignette interfaces. | 
| [SetVignetteCenter](色彩.md#setvignettecenter) | <span style="display:inline;color:#7575f9">客户端</span> | Set the vignetting center position of the vignetting (Vignette), which can change the position of the screen vignetting. | 
| [SetVignetteRGB](色彩.md#setvignettergb) | <span style="display:inline;color:#7575f9">客户端</span> | Set the vignetting (Vignette) color, which can change the screen vignetting color. | 
| [SetVignetteRadius](晕.md#setvignetteradius) | <span style="display:inline;color:#7575f9">Client</span> | Set the vignetting radius of the vignetting. The larger the radius, the smaller the vignetting and the larger the player's field of view. | 
| [SetVignetteSmoothness](晕.md#setvignettesmoothness) | <span style="display:inline;color:#7575f9">Client</span> | Set the vignetting blur coefficient of vignetting (Vignette). The larger the blur coefficient, the blurrier the vignetting edge and the larger the blur range. | 

### Blur 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CheckGaussianBlurEnabled](模糊.md#checkgaussianblurenabled) | <span style="display:inline;color:#7575f9">Client</span> | Check whether the Gaussian blur effect is enabled. | 
| [SetEnableGaussianBlur](blur.md#setenablegaussianblur) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to enable the Gaussian blur effect. When enabled, the area around the player's screen is blurred. The effect parameters can be set through the Gaussian blur other interfaces. | 
| [SetGaussianBlurRadius](blur.md#setgaussianblurradius) | <span style="display:inline;color:#7575f9">Client</span> | Set the blur radius of the Gaussian blur effect. The larger the radius, the greater the blur, and vice versa. | 

### Color 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CheckColorAdjustmentEnabled](Color.md#checkcoloradjustmentenabled) | <span style="display:inline;color:#7575f9">Client</span> | Check whether the color correction effect is enabled. | 
| [SetColorAdjustmentBrightness](Color.md#setcoloradjustmentbrightness) | <span style="display:inline;color:#7575f9">Client</span> | Adjust the screen color brightness. The larger the brightness value, the brighter the screen, and vice versa. | 
| [SetColorAdjustmentContrast](Color.md#setcoloradjustmentcontrast) | <span style="display:inline;color:#7575f9">Client</span> | Adjust the screen color contrast. The larger the screen contrast value, the more obvious the color difference is, and vice versa. | 
| [SetColorAdjustmentSaturation](Color.md#setcoloradjustmentsaturation) | <span style="display:inline;color:#7575f9">Client</span> | Adjust the screen color saturation. The larger the screen saturation value, the more obvious the color is, and vice versa. | 
| [SetColorAdjustmentTint](Color.md#setcoloradjustmenttint) | <span style="display:inline;color:#7575f9">Client</span> | Adjust the tint of the screen color. Adjust the screen color according to the input tint and intensity. When the intensity is greater, the overall screen color is more biased towards the input tint. | 
| [SetEnableColorAdjustment](Color.md#setenablecoloradjustment) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to enable the color correction effect. After enabling, the screen color can be adjusted. The effect parameters can be set through the other interfaces of the color correction effect. | 

### Lens Effects 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CheckDepthOfFieldEnabled](LensEffects.md#checkdepthoffieldenabled) | <span style="display:inline;color:#7575f9">Client</span> | Check if the depth of field effect is enabled. | 
| [CheckLensStainEnabled](LensEffects.md#checklensstainenabled) | <span style="display:inline;color:#7575f9">Client</span> | Check if the lens stain effect is enabled. | 
| [ResetLensStainTexture](Lens Effects.md#resetlensstaintexture) | <span style="display:inline;color:#7575f9">Client</span> | Reset the texture used by the stain effect to the system default texture. | 
| [SetDepthOfFieldBlurRadius](Lens Effects.md#setdepthoffieldblurradius) | <span style="display:inline;color:#7575f9">Client</span> | Adjust the blur radius of the depth of field effect. The larger the blur radius, the greater the blur, and vice versa. |

| [SetDepthOfFieldFarBlurScale](LensEffects.md#setdepthoffieldfarblurscale) | <span style="display:inline;color:#7575f9">Client</span> | Adjust the far blur size of the depth of field effect. The larger the far blur size, the greater the blur of the far view, and vice versa. Note that the adjustment of the far blur depends on the focus distance. If the focus is at a closer distance, the far view is in a clearer state at this time, and the adjustment of the blur size will not be very obvious. | 
| [SetDepthOfFieldFocusDistance](LensEffects.md#setdepthoffieldfocusdistance) | <span style="display:inline;color:#7575f9">Client</span> | Adjust the focus distance of the depth of field effect. The smaller the distance, the blurrier the far view and the clearer the near view; the larger the distance, the clearer the far view and the blurrier the near view. This distance is the actual distance, that is, the world coordinate distance with the player's camera as the starting point. | 
| [SetDepthOfFieldNearBlurScale](LensEffects.md#setdepthoffieldnearblurscale) | <span style="display:inline;color:#7575f9">Client</span> | Adjust the near blur size of the depth of field effect. The larger the near blur size, the greater the blur of the near field, and vice versa. Note that the adjustment of the near blur depends on the focus distance. If the focus is at a closer distance, the near field is in a clearer state, and the adjustment of the blur size will not be very obvious. | 
| [SetDepthOfFieldUseCenterFocus](LensEffects.md#setdepthoffieldusecenterfocus) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the depth of field effect turns on the screen center focus mode. If turned on, the focus distance will be automatically set to the distance of the object corresponding to the center of the screen. In the first-person perspective, the focus distance will be automatically set to the distance between the object corresponding to the screen crosshair and the camera, that is, the object corresponding to the crosshair will be automatically focused. In the third-person perspective, since the center of the screen always corresponds to the player, the focus distance will be automatically set to the distance between the player and the camera, that is, the player will be automatically focused on himself. | 
| [SetEnableDepthOfField](Lens Effect.md#setenabledepthoffield) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to enable the depth of field effect. When enabled, the depth of field effect will appear on the screen, and the effect of blurring the distance and being clear near or blurring the near and being clear at a distance will appear according to the focus distance. | 
| [SetEnableLensStain](Lens Effect.md#setenablelensstain) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to enable the lens stain effect. When enabled, the lens will have a stain effect, and the stain map and stain color used can be changed. | 
| [SetLensStainColor](LensEffect.md#setlensstaincolor) | <span style="display:inline;color:#7575f9">Client</span> | Adjust the lens stain color. Adjust the stain color according to the input color and intensity. When the intensity is greater, the stain color is more biased towards the input color. | 
| [SetLensStainIntensity](LensEffect.md#setlensstainintensity) | <span style="display:inline;color:#7575f9">Client</span> | Adjust the lens stain intensity. The greater the intensity, the more obvious the stain, and vice versa. | 
| [SetLensStainTexture](LensEffect.md#setlensstaintexture) | <span style="display:inline;color:#7575f9">Client</span> | After the lens stain effect is turned on, the stain effect uses the system default texture. This interface can change the texture used for lens stains. Note that it is best to use a transparent background for the texture, otherwise the screen will be covered by the texture. | 

