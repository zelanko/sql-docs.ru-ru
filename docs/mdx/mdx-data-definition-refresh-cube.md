---
title: "Инструкция REFRESH CUBE (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Cube
- REFRESH CUBE
- REFRESH_CUBE
- REFRESH
dev_langs: kbMDX
helpviewer_keywords:
- cubes [Analysis Services], cache
- refreshing cache
- REFRESH CUBE statement
- cache [Analysis Services]
ms.assetid: b8c087fb-5d17-4b13-b7cf-9929e9aab35c
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 37649d37d1cef67eb50caf8f3768beba19545988
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
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
  
## <a name="remarks"></a>Remarks  
 Для клиентских приложений, подключенных к экземпляру [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], эта инструкция вызывает кэшированные в клиентское приложение для синхронизации с сервером. Хотя обычно такие обновления производятся автоматически, отрезок времени до следующего обновления зависит от параметров строки соединения клиента. Инструкция REFRESH CUBE обновляет данные немедленно.  
  
 Для клиентских приложений, подключенных к локальному кубу, инструкция REFRESH CUBE перестраивает файл локального куба.  
  
> [!IMPORTANT]  
>  Именованные наборы, хранящиеся на сервере, не обновляются.  
  
## <a name="see-also"></a>См. также:  
 [Инструкции определения данных &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
