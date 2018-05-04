---
title: Параметры (базы данных Azure SQL) проекта (MySQLToSQL) | Документы Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
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
ms.assetid: 8c06420a-533b-4de0-948d-a0c6b368c544
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: b8e0ba412e7d29c2177579da04ed6557200d61fc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="project-settings-azure-sql-db-mysqltosql"></a>Параметры (базы данных Azure SQL) проекта (MySQLToSQL)
Параметры проекта SQL Azure позволяют настраивать суффикс базы данных SQL Azure, добавляется в диалоговом окне соединения, а также позволяют реализовывать механизм пульса в соединении с SQL Azure.  
  
Панель SQL Azure доступна в **параметры проекта** и **параметры проекта по умолчанию** диалоговым окнам.  
  
-   Используйте диалоговое окно параметров проекта, чтобы задать параметры конфигурации для текущего проекта. Для доступа к параметрам SQL Azure, на **средства** последовательно выберите пункты **параметры проекта**, нажмите кнопку **Общие** в нижней части левой панели, а затем выберите **SQL Azure**.  
  
-   Используйте диалоговое окно Параметры проекта по умолчанию, чтобы задать параметры конфигурации для всех проектов. Для доступа к параметрам SQL Azure, на **средства** последовательно выберите пункты **параметры DefaultProject**, выберите тип проекта миграции как SQL Azure из **миграции целевой версии** раскрывающийся список, чтобы получить доступ к настройкам на панели SQL Azure, нажмите кнопку **Общие** в нижней части левой панели, а затем выберите **SQL Azure**.  
  
## <a name="options"></a>Параметры  
  
## <a name="connectivity"></a>Соединение  
**Интервал подтверждения соединения**  
  
Задает интервал времени, используемый для периодического сигнала механизм для сохранения подключение к SQL Azure в "минуты: секунды формат.  
  
**Значение по умолчанию**: "4:45 '  
  
Значение должно быть указано в am: формата ss (например, "4:45 ' или ' 0:50 ').  
  
**Суффикс сервера Azure SQL**  
  
Задает суффикс сервера SQL Azure  
  
**Значение по умолчанию**: «database.windows.net».  
  
