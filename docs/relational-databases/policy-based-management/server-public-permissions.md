---
title: Разрешения роли сервера public | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4d600a5bf3e5667fdd3bd247e2e479a6c870ff21
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68021712"
---
# <a name="server-public-permissions"></a>Разрешения роли сервера public
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Это правило определяет, имеет ли роль сервера public разрешения на сервер. Каждое создающееся на сервере имя входа является членом роли сервера public. Если это условие выполняется, все имена входа на сервере будут иметь разрешение на сервер.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Не предоставляйте серверной роли public разрешения на сервер.  
  
> [!IMPORTANT]  
>  После завершения программы установки роль **PUBLIC** имеет разрешение **CONNECT** на всех конечных точках, за исключением **Dedicated Admin Connection**. Это нормально, и в обычных ситуациях не нуждается в изменении. (Управление доступом осуществляется с помощью разрешения **CONNECT SQL** , которое предоставляется автоматически при создании нового имени входа.)  
  
### <a name="for-more-information"></a>Дополнительные сведения  
 [Обеспечение безопасности SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
  
