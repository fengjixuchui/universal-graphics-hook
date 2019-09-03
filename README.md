# universal-graphics-hook
A cpp project developed for hooking various graphic libraries such as: d3d9, d3d10, d3d11, d3d12, gdi, gdi+, opengl and vulkan.

dllmain includes examples for all of the listed libraries except gdi & gdi+ as not all features have been implemented.

## Example
![d3d11 example](https://i.gyazo.com/86a02a5ef9430a0ce9c572c75b8df2cc.png)

## Usage
The included header file contains almost all method tables for the supported libraries to be hooked.

### Basic Example for D3D9
```c++
typedef HRESULT(__stdcall* d3d9Present)(LPDIRECT3DDEVICE9);
typedef HRESULT(__stdcall* d3d9EndScene)(LPDIRECT3DDEVICE9);

static d3d9Present g_od3d9Present = nullptr;
static d3d9Present g_od3d9EndScene = nullptr;

HRESULT __stdcall hkd3d9Present
(
	LPDIRECT3DDEVICE9 pDevice
)
{
	return g_od3d9Present(pDevice);
}

HRESULT __stdcall hkd3d9EndScene
(
	LPDIRECT3DDEVICE9 pDevice
)
{
	return g_od3d9EndScene(pDevice);
}

int thread()
{
	if (init() == Success)
	{
		GraphicsType render_type = getRenderType();

		switch (render_type) {
		case D3D9:
			bind(17, (void**)& g_od3d9Present, hkd3d9Present);
			bind(42, (void**)& g_od3d9EndScene, hkd3d9EndScene);
			break;
		case D3D10:
			break;
		case D3D11:
			break;
		case D3D12:
			break;
		case GDI:
			break;
		case GDIPLUS:
			break;
		case OpenGL:
			break;
		case Vulkan:
			break;
		}
	}

	do {
		Sleep(100);
	} while (!(GetAsyncKeyState(VK_END) & 0x1));

	exit(-1);

	return 0;
}

BOOL WINAPI DllMain
(
	HINSTANCE hInstance,
	DWORD dwReason,
	LPVOID lpReserved
)
{
	DisableThreadLibraryCalls(hInstance);

	switch (dwReason)
	{
	case DLL_PROCESS_ATTACH:
		CreateThread(NULL, 0, (LPTHREAD_START_ROUTINE)thread, NULL, 0, NULL);
		break;

		return TRUE;
	}
}
```

### Debugging
To disable / enable debuggin console, then just change (https://github.com/alxbrn/universal-graphics-hook/blob/master/ug.h#L28):
```c++
#define UG_DEBUG 1
```

1 = Debugging enabled,
0 = Debugging disabled

## Credits / Inspired by
evolution536 & Rebzzel

### Enjoy!
