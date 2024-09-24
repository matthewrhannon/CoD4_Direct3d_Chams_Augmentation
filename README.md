# CoD4_Direct3d_Chams_Augmentation
Direct3D Chams for Call of Duty 4 Direct3D wrapper using CRC checksums to isolate wanted materials.

# Summary
This is a game enhancer which was designed around one of the early releases of Call of Duty 4
(COD4). It functions independent of the game code, and instead utilizes COD4’s dependence on DirectX
for graphics. The binary for this project, a dynamic link file (DLL), is injected into the COD4’s process,
where it intercepts the function ‘Direct3DCreate9’, and takes control over the Direct3DDevice9 class.
The functions inside of this class where are altered before calling the original function are SetTexture,
DrawIndexedPrimitive, and CreateTexture. A cyclic redundancy check (CRC) is computed for each
texture, and this CRC value is later compared inside of DrawIndexedPrimitive which is the primary
function used to render geometry on the screen for COD4. This value is compared against predetermined 
CRC values which represent the texture checksum for the uniforms that the soldiers in the
game are wearing. If both checksums match, then that texture is altered to a very easy to notice color
before actually drawing it on the screen. Furthermore depth testing is disabled which makes it so you
can see the enemy through walls.

# Usage
This DLL can be injected into COD4 using any public DLL Injector. However this application was
designed around an early version of COD4 so whether or not it works with other versions is unknown.
Once in game, press F11 to turn on the functionality.
