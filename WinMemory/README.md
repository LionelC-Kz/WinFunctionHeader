# WinFunctionHeader

This header should be included to your C++ Project by

	#inclde "Mziller.h"
	
Object can be created by

	Mziller* mz = new Mziller;

For using the memory function should declare some variable by

	HWND g_hwnd;
	HANDLE g_processHANDLE;
	DWORD g_pid;

For finding the windows handle can find it by the windows' name

	g_hwnd = ::FindWindow(L"ClassName", L"WindowsName");
	
Or find it by the mousepoint 

	g_hwnd = mz.GetMousePointWindow()

Find the ProcessID by

	GetWindowThreadProcessId(g_hwnd, &g_pid);
	
Find the Process Handle by

	g_processHANDLE = OpenProcess(PROCESS_ALL_ACCESS, false, g_pid);
	
Function demo
In 32bits enviroment:

	DWORD value;
	mz->WriteMemory(&value, g_processHANDLE, 0x75B424, 0x44, 0x68, 0x768, 0x1c, 0x555c, endoffset);
	
	BYTE set = {0x12, 0x1b}
	mz->WriteMemory(&set, g_processHANDLE, 0x75B424);
	
	DWORD value;
	mz->ReadMemory(value, g_processHANDLE, 0x75B424,0x44, 0x68, 0x768, 0x1c, 0x555c, endoffset);
	mz->ReadMemory(value, g_processHANDLE, 0x75B424);
	
	DWORD address;
	mz->GetMemoryAddress(value, g_processHANDLE, 0x75B424, 0x44, 0x68, 0x768, 0x1c, endoffset);
	DWORD minesweeperbase = GetModuleBase(L"minesweeper.exe", g_pid);
	
In 64bits enviroment:

	DWORD value;
	mz->WriteMemory64(&value, g_processHANDLE, (DWORD64)0x75B424, (DWORD64)0x44, (DWORD64)0x68, (DWORD64)0x768, (DWORD64)0x1c, (DWORD64)0x555c, endoffset64);
	
	BYTE set = {0x12, 0x1b}
	mz->WriteMemory64(&set, g_processHANDLE, (DWORD64)0x75B424);
	
	DWORD value;
	mz->ReadMemory64(value, g_processHANDLE, (DWORD64)0x75B424,(DWORD64)0x44, (DWORD64)0x68, (DWORD64)0x768, (DWORD64)0x1c, (DWORD64)0x555c, endoffset64);
	mz->ReadMemory64(value, g_processHANDLE, (DWORD64)0x75B424);
	
	DWORD address;
	mz->GetMemoryAddress64(value, g_processHANDLE, (DWORD64)0x75B424, (DWORD64)0x44, (DWORD64)0x68, (DWORD64)0x768, (DWORD64)0x1c, endoffset64);
	DWORD minesweeperbase = GetModuleBase64(L"minesweeper.exe", g_pid);
	

