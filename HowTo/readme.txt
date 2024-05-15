https://learn.microsoft.com/en-us/windows/win32/eventlog/reporting-an-event

To compile the message text file, use the following command:

mc -U provider.mc

To compile the resources that the message compiler generated, use the following command:

rc provider.rc

To create the resource-only DLL that contains the message table string resources, use the following command (you can run the command from a Visual Studio Command Prompt):

link -dll -noentry provider.res

Before running this example, register the provider in the registry. For details on the registry settings, see Event Sources. Add "MyEventProvider" as a registry key under the following key:

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\eventlog\Application

The following shows the registry values to set for the "MyEventProvider" registry key.

Value name	Type	Value data
CategoryCount	REG_DWORD	0x00000003
CategoryMessageFile	REG_SZ	path\provider.dll
EventMessageFile	REG_SZ	path\provider.dll
ParameterMessageFile	REG_SZ	path\provider.dll
TypesSupported	REG_DWORD	0x00000007