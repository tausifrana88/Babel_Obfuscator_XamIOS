# Babel_Obfuscar

This GitHub repository provides a comprehensive example of Babel Obfuscator for Xamarin IOS 

Steps to Obfuscate Code:

1. Create Xamarin single view application project (IOS)

2. Add babel.Obfuscator nuget package to local folder (<a href="https://www.babelfor.net/downloads/">Babel.Obfuscator.10.8.0</a>)

3. Add babel configuration to projects .csproj file

4. Build Project

If project is successfully build then .dll file with given project name is generated on given path

IOS     : /bin/Release/net8.0-ios/ios-arm64/Babel_Obfuscator_XamIOS.dll 

Notes: The given configuration generated an error and does not obfuscate a code

Configuration 1: 

<UsingTask TaskName="Babel" AssemblyFile="$(ProjectDir)Babel\Babel.Build.dll" />

<Target Name="Obfuscate" AfterTargets="Compile">
    <Babel InputFile="$(ProjectDir)$(IntermediateOutputPath)$(TargetFileName)" OutputFile="$(ProjectDir)$(IntermediateOutputPath)$(TargetFileName)" ObfuscateTypes="true" ObfuscateEvents="true" ObfuscateMethods="true" ObfuscateProperties="true" ObfuscateFields="true" VirtualFunctions="true" UnicodeNormalization="true" FlattenNamespaces="true" OverloadedRenaming="true" StringEncryption="hash" ControlFLowObfuscation="if=on;switch=on;case=on;call=on" ControlFLowIterations="3" />
 </Target>

Error:
/Users/tausifrana/Documents/Github/Babel_Obfuscator_IOS/Babel_Obfuscar_XamIOS/BABEL: Error: A valid license could not be found. Please contact https://www.babelfor.net for assistance. (Babel_Obfuscar_XamIOS)

Configuration 2:
 
 <Target Name="AfterBuild">
    <Babel InputFile="$(TargetPath)/Babel_Obfuscar_XamIOS.dll" OutputFile="$(TargetPath)/Babel_Obfuscar_XamIOS.dll" ObfuscateTypes="true" ObfuscateEvents="true" ObfuscateMethods="true" ObfuscateProperties="true" ObfuscateFields="true" VirtualFunctions="true" UnicodeNormalization="true" FlattenNamespaces="true" OverloadedRenaming="true" StringEncryption="hash" ControlFLowObfuscation="if=on;switch=on;case=on;call=on" ControlFLowIterations="3" />
 </Target>

Error:
/Users/tausifrana/Documents/Github/Babel_Obfuscator_IOS/Babel_Obfuscar_XamIOS/Babel_Obfuscar_XamIOS.csproj(6,6): Error MSB4036: The "Babel" task was not found. Check the following: 1.) The name of the task in the project file is the same as the name of the task class. 2.) The task class is "public" and implements the Microsoft.Build.Framework.ITask interface. 3.) The task is correctly declared with <UsingTask> in the project file, or in the *.tasks files located in the "/Applications/Visual Studio.app/Contents/MonoBundle/MSBuild/Current/bin" directory. (MSB4036) (Babel_Obfuscar_XamIOS)
