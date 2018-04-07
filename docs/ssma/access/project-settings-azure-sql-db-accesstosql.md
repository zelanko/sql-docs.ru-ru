---
title: Параметры (базы данных Azure SQL) проекта (AccessToSQL) | Документы Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-access
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Project Settings dialog box, SQL Azure
- SQL Azure settings
ms.assetid: bbb8a204-d0e4-4f0b-9709-271feb1f136e
caps.latest.revision: 11
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ca33c5cfd48b8ebc9c9b98bd6a0b606fec61ef96
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="project-settings-azure-sql-db-accesstosql"></a>Параметры (базы данных Azure SQL) проекта (AccessToSQL)
Параметры проекта SQL Azure позволяют настраивать суффикс базы данных SQL Azure, добавляется в диалоговом окне соединения, а также позволяют реализовывать механизм пульса в соединении с SQL Azure.  
  
Панель SQL Azure доступна в **параметры проекта** и **параметры проекта по умолчанию** диалоговым окнам.  
  
-   Используйте диалоговое окно параметров проекта, чтобы задать параметры конфигурации для текущего проекта. Для доступа к параметрам SQL Azure, на **средства** последовательно выберите пункты **параметры проекта**, нажмите кнопку **Общие** в нижней части левой панели, а затем выберите **SQL Azure**.  
  
-   Используйте диалоговое окно Параметры проекта по умолчанию, чтобы задать параметры конфигурации для всех проектов. Для доступа к параметрам SQL Azure, на **средства** последовательно выберите пункты **параметры DefaultProject**, выберите тип проекта как «SQL Azure» в **миграции целевой версии** щелкните поле со списком для доступа к параметрам в области SQL Azure **Общие** в нижней части левой панели, а затем выберите **SQL Azure**.  
  
## <a name="options"></a>Параметры  
  
## <a name="connectivity"></a>Соединение  
**Интервал подтверждения соединения**  
  
Задает интервал времени, используемый для периодического сигнала механизм для сохранения подключение к SQL Azure в "минуты: секунды формат.  
  
**Значение по умолчанию**: "4:45 '  
  
Значение должно быть указано в am: формата ss (например, "4:45 ' или ' 0:50 ').  
  
**Суффикс сервера Azure SQL**  
  
Задает суффикс сервера SQL Azure  
  
**Значение по умолчанию**: «database.windows.net».  
  
