# ZKTecoAttLogsDemo
This is a demo of how to fetch the Attendance Logs from a ZKTeco Clock UA860 (https://www.zkteco.com/en/product_detail/UA860.html).

This sample was made in Visual Studio 2017 using .Net Framework 4.7.2. and zkemkeeper.dll


# Links

Here you can download the .zip for the Standalone SDK 6.3.1.37( Include Pull SDK 2.2.0.219).

[SDK](https://www.zkteco.com/en/download_catgory/46.html)

This zip contains code examples (this is the one in the "new" folder, I have just adapted it to VS2017) and the SDK for C# used here.

(I have copied the whole .zip into the root of this folder)

# How to run

1. Go to the folder called SDK-Ver6.3.1.37 and depending on the operative system go to 64bits or 32bits
1.1 Run as Admin the batch file Register_SDK_x86.bat or Register_SDK_x64.bat tp install de required dlls (see below for common issues on this).
1. ...


# Add the reference to Visual Studio 64bits issue

If you are trying to run the code in Visual Studio (I'm using VS 2017) something weird always happens, since VS is a 32bits app whenever
you try to add the reference of `zkemkeeper` to the project the directory `System32` will be swapped to `SysWOW64`.

So, when you are looking for the reference in Visual Studio and you try to open
`C:\Windows\System32` you will actually see the directory `C:\Windows\SysWOW64`

To solve this just copy all the `.dll` files in `SDK-Ver6.3.1.37\64bits to C:\Windows\SysWOW64`
Then run `regsvr32 C:\Windows\SysWOW64\zkemkeeper.dll`

Now you can add the reference in Visual Studio to C:\Windows\System32\zkemkeeper.dll.
(but internally it will be pointing to C:\Windows\SysWOW64\zkemkeeper.dll)

UPDATE: Actually I have modified the provided .bat file to do this, Jjust run Register_SDK_x64_SysWOW64.bat and it will copy an register into SysWOW64.

`Mmdas si ya se.`

# Interop Type cannot be Embedded issue (visual studio)

This issue may be presented in Visual Studio after adding zkemkeeper.dll as reference.

To solve it just open the Properties window for zkemkeeper reference (double click on it or right click -> Properties) and change the Property `Embed Interop Types` to `false`

https://stackoverflow.com/questions/2483659/interop-type-cannot-be-embedded