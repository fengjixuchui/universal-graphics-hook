# universal-graphics-hook
A cpp project developed for hooking various graphic libraries such as: d3d9, d3d10, d3d11, d3d12, gdi, gdi+, opengl and vulkan. (Inspired by Kiero)

dllmain includes examples for all of the listed libraries except gdi & gdi+ as not all features have been implemented.

## Example
![d3d11 example](https://i.gyazo.com/86a02a5ef9430a0ce9c572c75b8df2cc.png)

## Usage
The included header file contains almost all method tables for the supported libraries to be hooked.

To disable / enable debuggin console, then just change (https://github.com/alxbrn/universal-graphics-hook/blob/master/ug.h#L28):
```c++
#define UG_DEBUG 1
```

1 = Debugging enabled,
0 = Debugging disabled

## Credits / Inspired by
evolution536 & Rebzzel

### Enjoy!
