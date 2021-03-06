---
title: '#<a name="region-directive"></a>Dyrektywy regionu'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb308da6ad0ca6243f14e0d825ed7eb005d622bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="region-directive"></a>#Region — dyrektywa
Zwija i ukrywa sekcje kodu w plikach języka Visual Basic.  
  
## <a name="syntax"></a>Składnia  
  
```  
      #Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`identifier_string`|Wymagany. Ciąg, który działa jako tytuł regionu, gdy jest zwinięte. Regiony są zwijane domyślnie.|  
|`#End Region`|Kończy `#Region` bloku.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj `#Region` dyrektywy bloku kodu, aby rozwinąć lub zwinąć podczas korzystania z funkcji zwijania edytora kodu programu Visual Studio. Można umieścić lub *zagnieździć*, regionów, w ramach innych regionów, do grupowania podobnych regionów.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `#Region` dyrektywy.  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [#If... Then... #Else — dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Tworzenie konspektu](/visualstudio/ide/outlining)  
 [Porady: zwijanie i ukrywanie fragmentów kodu](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
