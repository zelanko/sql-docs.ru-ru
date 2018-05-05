---
title: Обновление из базы данных (AccessToSQL) | Документы Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-access
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 3b671f49-c4cc-44fd-801e-e738a8c79415
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: bebc8ce1f40475d559b52f9b863ab9add09d0168
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="refresh-from-database-accesstosql"></a>Обновление из базы данных (AccessToSQL)
**Обновление из базы данных** диалоговое окно позволяет выбрать объекты для обновления из базы данных Access. Строки в диалоговом окне отображаются цветовые обозначения, исходя из состояния метаданных:  
  
-   Если метаданные объекта был изменен локально и в базе данных Access, строки — синим.  
  
-   Если метаданные объекта был изменен в базе данных Access, но не в SSMA, желтый строки.  
  
-   Если метаданные объекта изменилось локально, но не в базе данных Access, строка имеет зеленый цвет.  
  
-   Если объект является новой базы данных Access, строки розовым цветом.  
  
Можно указать параметры обновления объекта по умолчанию в **параметры проекта** диалоговое окно. Дополнительные сведения см. в разделе [параметры проекта &#40;загрузке объектов&#41; &#40;AccessToSQL&#41;](../../ssma/access/project-settings-loading-objects-accesstosql.md)  
  
Для доступа к **обновление из базы данных** диалогового окна щелкните правой кнопкой любой **базы данных** в обозревателе метаданных доступ, щелкните **обновление из базы данных**.  
  
