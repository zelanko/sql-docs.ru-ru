---
description: Использование служб Microsoft IIS
title: Использование Microsoft службы IIS | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], IIS
- internet information services [ODBC]
- IIS [ODBC]
ms.assetid: 3328f2f1-b34a-472f-82cf-ad49768ff061
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e20a15aad4409f535d83e813fdfbd911ca80674
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471336"
---
# <a name="using-microsoft-internet-information-services"></a>Использование служб Microsoft IIS
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 Если у вас возникли трудности при подключении из скрипта IIS (особенно при получении ошибки ORA-12641), добавьте следующую строку в файл Склнет. ORA:  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```  
  
 Это отключит защищенные сетевые службы, чтобы вы могли подключаться с помощью анонимной проверки подлинности.
