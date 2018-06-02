---
title: Инструкции CALL (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b8610a0ed7fc0c90fb3e8c684b33b466eb3858f9
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580106"
---
# <a name="mdx-data-manipulation---call"></a>Управление данными MDX - ВЫЗОВ
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Выполняет хранимую процедуру, которая возвращает значение void в текущей области или (по желанию) в указанном кубе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CALL SP_Name   
   [ (SP_Argument   
      [, SP_Argument ,...n]  
      ) ]   
[ONCube_Expression]  
```  
  
## <a name="arguments"></a>Аргументы  
 *SP_Name*  
 Допустимое строковое выражение, представляющее имя хранимой процедуры.  
  
 *SP_Argument*  
 Допустимое строковое выражение, представляющее аргумент хранимой процедуры.  
  
 *Cube_Expression*  
 Допустимое строковое выражение куба, представляющее имя куба.  
  
## <a name="remarks"></a>Примечания  
 **ВЫЗОВИТЕ** инструкция запускает указанный регистрируемой хранимой процедуры, включая при необходимости один или несколько аргументов для указанной хранимой процедуры. **ВЫЗОВИТЕ** инструкция предназначена для использования только с помощью хранимых процедур, возвращающих значение void. Ее нельзя сочетать с другими функциями и операторами в многомерном выражении. Зарегистрированные хранимые процедуры, возвращающие значения, можно явно вызывать в многомерных выражениях и использовать совместно с другими функциями и операторами многомерных выражений.  
  
 Если куб не указан, инструкция выполняет хранимую процедуру над текущим кубом.  
  
> [!NOTE]  
>  Если хранимая процедура не зарегистрирована на компьютере клиента, **вызвать** оператор пытается вызвать хранимую процедуру из экземпляра [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Инструкции языка манипулирования данными &#40;многомерных Выражений&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [Использование хранимых процедур (MDX)](../mdx/using-stored-procedures-mdx.md)  
  
  
