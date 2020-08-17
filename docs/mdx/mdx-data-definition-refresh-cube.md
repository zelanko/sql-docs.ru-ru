---
description: Определение данных многомерных выражений — REFRESH CUBE
title: Инструкция обновления куба (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 05ae95c97ae21d3b8ff7b4e457cf3ddf8cc38989
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387058"
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
  
## <a name="remarks"></a>Remarks  
 Для клиентских приложений, подключенных к экземпляру [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , эта инструкция вызывает синхронизацию памяти, кэшированной в клиентском приложении, с сервером. Хотя обычно такие обновления производятся автоматически, отрезок времени до следующего обновления зависит от параметров строки соединения клиента. Инструкция REFRESH CUBE обновляет данные немедленно.  
  
 Для клиентских приложений, подключенных к локальному кубу, инструкция REFRESH CUBE перестраивает файл локального куба.  
  
> [!IMPORTANT]  
>  Именованные наборы, хранящиеся на сервере, не обновляются.  
  
## <a name="see-also"></a>См. также:  
 [Инструкции определения данных многомерных выражений &#40;&#41;многомерных выражений ](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
