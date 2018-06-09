---
title: Обновление из базы данных (AccessToSQL) | Документы Microsoft
ms.prod: sql
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
ms.openlocfilehash: 6d38b1bdb437ed553648d9f93c0b09edfc7ca463
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34774100"
---
# <a name="refresh-from-database-accesstosql"></a>Обновление из базы данных (AccessToSQL)
**Обновление из базы данных** диалоговое окно позволяет выбрать объекты для обновления из базы данных Access. Строки в диалоговом окне отображаются цветовые обозначения, исходя из состояния метаданных:  
  
-   Если метаданные объекта был изменен локально и в базе данных Access, строки — синим.  
  
-   Если метаданные объекта был изменен в базе данных Access, но не в SSMA, желтый строки.  
  
-   Если метаданные объекта изменилось локально, но не в базе данных Access, строка имеет зеленый цвет.  
  
-   Если объект является новой базы данных Access, строки розовым цветом.  
  
Можно указать параметры обновления объекта по умолчанию в **параметры проекта** диалоговое окно. Дополнительные сведения см. в разделе [параметры проекта &#40;загрузке объектов&#41; &#40;AccessToSQL&#41;](../../ssma/access/project-settings-loading-objects-accesstosql.md)  
  
Для доступа к **обновление из базы данных** диалогового окна щелкните правой кнопкой любой **базы данных** в обозревателе метаданных доступ, щелкните **обновление из базы данных**.  
  
