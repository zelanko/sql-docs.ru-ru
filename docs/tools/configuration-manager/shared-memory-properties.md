---
title: Свойства общей памяти
description: Узнайте, как включить или отключить протокол общей памяти, который клиенты могут использовать для подключения к экземпляру SQL Server, работающему на том же компьютере.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 463ccd2c76d5b3dc1428aa35540f068eee7fcc37
ms.sourcegitcommit: 6d53ecfdc463914f045c20eda96da39dec22acca
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/26/2020
ms.locfileid: "88901091"
---
# <a name="shared-memory-properties"></a>Свойства общей памяти
[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]
  Используйте страницу **Протокол**в диалоговом окне **Свойства общей памяти** , чтобы включить или выключить протокол общей памяти. Общая память является простейшим протоколом и не имеет настраиваемых параметров. Поскольку клиенты, использующие протокол общей памяти, могут подключаться только к экземпляру [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], запущенному на том же компьютере, этот протокол не подходит для большинства операций с базами данных. Используйте протокол общей памяти, чтобы устранить неполадки, если есть вероятность того, что другие протоколы настроены некорректно.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть перезапущен, чтобы включить или отключить протокол.  
  
## <a name="options"></a>Параметры  
 **Enabled**  
 Возможные значения: **Да** и **Нет**. По умолчанию протокол общей памяти включен.  
  
## <a name="see-also"></a>См. также:  
 [Выбор сетевого протокола](/previous-versions/sql/sql-server-2016/ms187892(v=sql.130))   
 [Создание допустимой строки соединения с использованием протокола общей памяти](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
