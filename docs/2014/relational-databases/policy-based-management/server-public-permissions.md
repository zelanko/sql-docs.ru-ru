---
title: Разрешения роли сервера public | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 11f478f9cbbdedd246b3b1468572b62b27c86e5b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48207916"
---
# <a name="server-public-permissions"></a>Разрешения роли сервера public
  Это правило определяет, имеет ли роль сервера public разрешения на сервер. Каждое создающееся на сервере имя входа является членом роли сервера public. Если это условие выполняется, все имена входа на сервере будут иметь разрешение на сервер.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Не предоставляйте серверной роли public разрешения на сервер.  
  
> [!IMPORTANT]  
>  После завершения установки **ОТКРЫТЫЙ** роль имеет `CONNECT` разрешение всех конечных точек за исключением **Dedicated Admin Connection**. Это нормально, и в обычных ситуациях не нуждается в изменении. (Доступ контролируется с помощью `CONNECT SQL` разрешение, которое предоставляется автоматически при создании новых имен входа.)  
  
### <a name="for-more-information"></a>Дополнительные сведения  
 [Обеспечение безопасности SQL Server](../security/securing-sql-server.md)  
  
  
