---
title: sbyte - C# 参考
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- sbyte_CSharpKeyword
- sbyte
helpviewer_keywords:
- sbyte keyword [C#]
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
ms.openlocfilehash: df184bf32fa09b10c7f3de508ffb73b9cf156b92
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663397"
---
# <a name="sbyte-c-reference"></a>sbyte（C# 参考）

`sbyte` 表示一种整型类型，该类型根据下表显示的大小和范围存储值。  
  
|类型|范围|大小|.NET 类型|  
|----------|-----------|----------|-------------------------|  
|`sbyte`|-128 到 127|8 位带符号整数|<xref:System.SByte?displayProperty=nameWithType>|  
  
## <a name="literals"></a>文本  

可以通过为其分配十进制文本、十六进制文本或（从 C# 7.0 开始）二进制文本来声明和初始化 `sbyte` 变量。 

在以下示例中，等于 -102、表示为十进制、十六进制和二进制文本的整数从 [int](../../../csharp/language-reference/keywords/int.md) 转换为 `sbyte` 值。    
  
[!code-csharp[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]  

> [!NOTE] 
> 使用前缀 `0x` 或 `0X` 表示十六进制文本，使用前缀 `0b` 或 `0B` 表示二进制文本。 十进制文本没有前缀。

从 C# 7.0 开始，添加了一些功能以增强可读性。 
 - C# 7.0 允许将下划线字符 (`_`) 用作数字分隔符。
 - C# 7.2 允许将 `_` 用作二进制或十六进制文本的数字分隔符，位于前缀之后。 十进制文本不能够有前导下划线。

 下面是一些示例。

[!code-csharp[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]  

如果整数文本在 `sbyte` 范围之外（即，如果它小于 <xref:System.SByte.MinValue?displayProperty=nameWithType> 或大于 <xref:System.SByte.MaxValue?displayProperty=nameWithType>），会发生编译错误。 如果整数文本没有后缀，则其类型为以下类型中可表示其值的第一个类型：[int](int.md)、[uint](uint.md)、[long](long.md)、[ulong](ulong.md)。 这意味着，在此示例中，数字文本 `0x9A` 和 `0b10011010` 被解释为值为 156 的 32 位带符号整数，该值超过了 <xref:System.SByte.MaxValue?displayProperty=nameWithType>。 因此，需要使用强制转换运算符，并且赋值必须在[取消选中](unchecked.md)的上下文中发生。 

## <a name="compiler-overload-resolution"></a>编译器重载解析

 调用重载方法时必须使用强制转换。 以下面使用 `sbyte` 和 [int](../../../csharp/language-reference/keywords/int.md) 参数的重载方法为例：  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 使用 `sbyte` 强制转换可保证调用正确的类型，例如：  
  
```csharp 
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## <a name="conversions"></a>转换  
 存在从 `sbyte` 到 [short](../../../csharp/language-reference/keywords/short.md)、[int](../../../csharp/language-reference/keywords/int.md)、[long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 的预定义隐式转换。  
  
 不能将存储大小更大的非文本数值类型隐式转换为 `sbyte` 类型（有关整型类型的存储大小的信息，请参阅[整型类型表](../../../csharp/language-reference/keywords/integral-types-table.md)）。 以下面两个 `sbyte` 变量 `x` 和 `y` 为例：  
  
```csharp  
sbyte x = 10, y = 20;  
```  
  
 以下赋值语句会生成一个编译错误，原因是赋值运算符右侧的算术表达式在默认情况下的计算结果为 [int](../../../csharp/language-reference/keywords/int.md)。  
  
```csharp  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 若要更正此问题，请对该表达式执行强制转换，如以下示例所示：  
  
```csharp  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 但是，在目标变量具有相同或更大的存储大小时，可以使用下列语句：  
  
```csharp
sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 另请注意，不存在从浮点类型到 `sbyte` 类型的隐式转换。 例如，除非使用显式强制转换，否则以下语句将生成编译器错误：  
  
```csharp  
sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 有关兼用浮点类型和整型类型的算术表达式的信息，请参阅 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。  
  
 有关隐式数值转换规则的详细信息，请参阅[隐式数值转换表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。  
  
## <a name="c-language-specification"></a>C# 语言规范  

有关详细信息，请参阅 [C# 语言规范](../language-specification/index.md)中的[整型类型](~/_csharplang/spec/types.md#integral-types)。 该语言规范是 C# 语法和用法的权威资料。
  
## <a name="see-also"></a>请参阅

- <xref:System.SByte>
- [C# 参考](../../../csharp/language-reference/index.md)
- [C# 编程指南](../../../csharp/programming-guide/index.md)
- [C# 关键字](../../../csharp/language-reference/keywords/index.md)
- [整型表](../../../csharp/language-reference/keywords/integral-types-table.md)
- [内置类型表](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [隐式数值转换表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [显式数值转换表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
