---
title: Инструкция REFRESH CUBE (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f27051d9e0fe1d0a6eb3d580548233eb9f073215
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579776"
---
# <a name="mdx-data-definition---refresh-cube"></a>Определение данных MDX - обновления КУБА
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Обновляет кэш клиента для куба.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
REFRESH CUBECube_Name   
```  
  
## <a name="arguments"></a>Аргументы  
 *Cube_Name*  
 Допустимое строковое выражение, представляющее имя куба.  
  
## <a name="remarks"></a>Примечания  
 Для клиентских приложений, подключенных к экземпляру [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], эта инструкция вызывает кэшированные в клиентское приложение для синхронизации с сервером. Хотя обычно такие обновления производятся автоматически, отрезок времени до следующего обновления зависит от параметров строки соединения клиента. Инструкция REFRESH CUBE обновляет данные немедленно.  
  
 Для клиентских приложений, подключенных к локальному кубу, инструкция REFRESH CUBE перестраивает файл локального куба.  
  
> [!IMPORTANT]  
>  Именованные наборы, хранящиеся на сервере, не обновляются.  
  
## <a name="see-also"></a>См. также  
 [Инструкции определения данных многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
