---
title: “ReDim”只能更改最右边的维度
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: d20d0374cd5183b6216d1c6e5b138256cf0a4f17
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738950"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a>“ReDim”只能更改最右边的维度
`ReDim` 语句尝试使用 `Preserve` 关键字来更改一个数组的维度，它不是最后一个维度。 使用 `Preserve`时，只能调整数组最后一个维度的大小。 对于其他所有维度，必须指定与现有数组相同的大小。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   删除 `Preserve` 关键字。  
  
## <a name="see-also"></a>请参阅
- [Visual Basic 中的数组](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [在 Visual Basic 中的数组维数](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim 语句](../../visual-basic/language-reference/statements/redim-statement.md)
- [Dim 语句](../../visual-basic/language-reference/statements/dim-statement.md)
