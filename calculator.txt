.assembly extern mscorlib{}
.assembly Calculator {}
.module Calculator.exe

.class public Program extends [mscorlib]System.Object
{

.method public static void MyMain(string[] args) cil managed
{
.entrypoint
.locals init(
[0] int32 firstNumber,
[1] int32 secondNumber,
[2] string operation,
[3] int32 result

)
ldstr "***************** WELCOME TO MY CALCULATOR *****************"
call void [mscorlib]System.Console::WriteLine(string)
ldstr " Enter First Number :"
call void [mscorlib]System.Console::WriteLine(string)
call string[mscorlib]System.Console::ReadLine()
call int32[mscorlib]System.Int32::Parse(string)
stloc.0

ldstr " Enter Second Number :  "
call void [mscorlib]System.Console::WriteLine(string)
call string[mscorlib]System.Console::ReadLine()
call int32[mscorlib]System.Int32::Parse(string)
stloc.1

ldstr " Choose operator : + - * /  "
call void [mscorlib]System.Console::WriteLine(string)
call string[mscorlib]System.Console::ReadLine()
stloc.2

ldstr " The result is :  "
call void [mscorlib]System.Console::WriteLine(string)
 

ldloc.2
ldstr "+"
call bool[mscorlib]System.String::Equals(string,string)
brfalse.s SUBTRACT

ldloc.0
ldloc.1
add
stloc.3
ldloc.3
call void[mscorlib]System.Console::WriteLine(int32)
 
SUBTRACT:
ldloc.2
ldstr "-"
call bool[mscorlib]System.String::Equals(string,string)
brfalse.s MULTIPLY
ldloc.0
ldloc.1
sub
stloc.3
br.s PRINT_RESULT



MULTIPLY:
ldloc.2
ldstr "*"
call bool[mscorlib]System.String::Equals(string,string)
brfalse.s DIVIDE

ldloc.0
ldloc.1
mul
stloc.3
br.s PRINT_RESULT


DIVIDE:
ldloc.2
ldstr "/"
call bool [mscorlib]System.String::Equals(string,string)
brfalse.s  INVALID_OPERATION
ldloc.0
ldloc.1
div
stloc.3
br.s PRINT_RESULT



 INVALID_OPERATION:
 ldstr "Invalid operation!"
  call void [mscorlib]System.Console::WriteLine(string)
  ret

PRINT_RESULT:
ldloc.3
call void[mscorlib]System.Console::WriteLine(int32)
ldstr "***************** END *****************"
call void[mscorlib]System.Console::WriteLine(string)
ret

}

}