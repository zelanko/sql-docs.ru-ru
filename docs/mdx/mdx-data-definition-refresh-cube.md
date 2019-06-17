---
title: Инструкция REFRESH CUBE (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dafc13dda1f8ecab1400a88d1ca66eff5f317e43
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63285083"
---
# <a name="mdx-data-definition---refresh-cube"></a>Определение данных многомерных выражений — REFRESH CUBE


  Обновляет кэш клиента для куба.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
REFRESH CUBECube_Name   
```  
  
## <a name="arguments"></a>Аргументы  
 *Cube_Name*  
 Допустимое строковое выражение, представляющее имя куба.  
  
## <a name="remarks"></a>Примечания  
 Для клиентских приложений, подключенных к экземпляру [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], эта инструкция вызывает, кэшированные в клиентском приложении для синхронизации с сервером. Хотя обычно такие обновления производятся автоматически, отрезок времени до следующего обновления зависит от параметров строки соединения клиента. Инструкция REFRESH CUBE обновляет данные немедленно.  
  
 Для клиентских приложений, подключенных к локальному кубу, инструкция REFRESH CUBE перестраивает файл локального куба.  
  
> [!IMPORTANT]  
>  Именованные наборы, хранящиеся на сервере, не обновляются.  
  
## <a name="see-also"></a>См. также  
 [Инструкции определения данных многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
