---
title: Разрешения роли сервера public | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6f240973def97dea739c21381f38dc366deb8920
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62691470"
---
# <a name="server-public-permissions"></a>Разрешения роли сервера public
  Это правило определяет, имеет ли роль сервера public разрешения на сервер. Каждое создающееся на сервере имя входа является членом роли сервера public. Если это условие выполняется, все имена входа на сервере будут иметь разрешение на сервер.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Не предоставляйте серверной роли public разрешения на сервер.  
  
> [!IMPORTANT]  
>  После завершения установки роль **Public** имеет `CONNECT` разрешение на все конечные точки, кроме **выделенного административного соединения**. Это нормально, и в обычных ситуациях не нуждается в изменении. (Управление доступом осуществляется с помощью разрешения `CONNECT SQL`, которое предоставляется автоматически при создании нового имени входа.)  
  
### <a name="for-more-information"></a>Дополнительные сведения  
 [Обеспечение безопасности SQL Server](../security/securing-sql-server.md)  
  
  
