## de4dot VG
A de4dot fork with full support for [VirtualGuard Protector](https://virtualguard.io/)  

*Refer to the blogpost for more information.*    
https://mrt4ntr4.github.io/VirtualGuard-P1/  

## Features
* Fixes control flow
* Fixes proxy calls
* Removes Anti-Debug methods
* Removes Anti-Tamper methods

### [Original README](README-orig.md)
---

## Samples

### Before (obfuscated control flow):
```csharp
MemoryStream memoryStream = new MemoryStream();
byte[] source;
try
{
	for (;;)
	{
		IL_9A2:
		uint num30 = 0xC871780U;
		for (;;)
		{
			uint num2;
			switch ((num2 = (num30 ^ 0x7C4718BDU)) % 6U)
			{
			case 0U:
			{
				source = memoryStream.ToArray();
				uint num31 = num2;
				uint[] array = new uint[5];
				array[0] = 0xC8U;
				array[1] = 0x1DEU - array[0];
				array[2] = 0x131U - array[1] + array[0];
				array[3] = 0xA5U + array[2] + array[1] - array[0];
				array[4] = 0x198U - array[3] - array[2] + array[1] + array[0];
				uint num32 = num31 / array[4];
				num30 = num32 - 0xFF2B6A6FU;
				continue;
			}
			case 2U:
			{
				uint num33 = num2;
				uint[] array = new uint[3];
				array[0] = 0x17DU;
				array[1] = 0x1FCU - array[0];
				array[2] = 0x3CDU - array[1] - array[0];
				uint num34 = num33 / array[2];
				num30 = num34 - 0xCFE18673U;
				continue;
			}
			case 3U:
				goto IL_9A2;
			case 4U:
			{
				uint num35 = num2;
				uint[] array = new uint[3];
				array[0] = 0x140U;
				array[1] = 0x1C2U - array[0];
				array[2] = 0x224U + array[1] - array[0];
				uint num36 = num35 / array[2];
				num30 = num36 - 0xDE1106F5U;
				continue;
			}
			case 5U:
			{
				deflateStream.CopyTo(memoryStream);
				uint num37 = num2;
				uint[] array = new uint[4];
				array[0] = 0xAFU;
				array[1] = 0xF5U + array[0];
				array[2] = 0x304U - array[1] - array[0];
				array[3] = 0xFFFFFDA1U + array[2] + array[1] + array[0];
				uint num38 = num37 / array[3];
				num30 = num38 - 0xAF527217U;
				continue;
			}
			}
			goto Block_14;
		}
	}
	Block_14:;
}
finally
{
	if (memoryStream != null)
	{
		for (;;)
		{
			IL_C61:
			uint num39 = 0x120BF13FU;
			for (;;)
			{
				uint num2;
				switch ((num2 = (num39 ^ 0x7C4718BDU)) % 4U)
				{
				case 1U:
				{
					uint num40 = num2;
					uint[] array = new uint[4];
					array[0] = 0x140U;
					array[1] = 0x36U + array[0];
					array[2] = 0x3AEU - array[1] - array[0];
					array[3] = 0xFFFFFD7CU + array[2] + array[1] + array[0];
					uint num41 = num40 / array[3];
					num39 = num41 - 0x90A8BA9BU;
					continue;
				}
				case 2U:
				{
					((IDisposable)memoryStream).Dispose();
					uint num42 = num2;
					uint[] array = new uint[5];
					array[0] = 0xE6U;
					array[1] = 0x1ADU - array[0];
					array[2] = 0x6EU - array[1] + array[0];
					array[3] = 0x1DDU - array[2] - array[1] + array[0];
					array[4] = 0x17AU + array[3] + array[2] - array[1] - array[0];
					uint num43 = num42 / array[4];
					num39 = num43 - 0xD08D6419U;
					continue;
				}
				case 3U:
					goto IL_C61;
				}
				goto Block_16;
			}
		}
		Block_16:;
	}
}
```

### After:
```csharp
byte[] source;
using (MemoryStream memoryStream = new MemoryStream())
{
	deflateStream.CopyTo(memoryStream);
	source = memoryStream.ToArray();
}
```
