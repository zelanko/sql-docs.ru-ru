---
title: Параметры проекта (база данных Azure SQL) (AccessToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Project Settings dialog box, SQL Azure
- SQL Azure settings
ms.assetid: bbb8a204-d0e4-4f0b-9709-271feb1f136e
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d10af49e419827f9fbd70b7cbef45fdf0562dea3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47749631"
---
# <a name="project-settings-azure-sql-db-accesstosql"></a>Параметры проекта (база данных Azure SQL) (AccessToSQL)
Параметры проекта SQL Azure позволяют настраивать суффикс базы данных SQL Azure для добавления в диалоговом окне соединения и позволяют реализации механизма пульса в соединении SQL Azure.  
  
На панели SQL Azure доступна в **параметры проекта** и **параметры проекта по умолчанию** диалоговым окнам.  
  
-   Используйте диалоговое окно параметров проекта, чтобы задать параметры конфигурации для текущего проекта. Для доступа к параметрам SQL Azure, на **средства** меню, выберите **параметры проекта**, нажмите кнопку **Общие** в нижней части левой панели, а затем выберите **SQL Azure**.  
  
-   Используйте диалоговое окно Параметры проекта по умолчанию, чтобы задать параметры конфигурации для всех проектов. Для доступа к параметрам SQL Azure, на **средства** меню, выберите **параметры DefaultProject**, выберите тип проекта как «SQL Azure» в **целевой версии миграции** поле со списком для доступа к параметрам в области SQL Azure, щелкните **Общие** в нижней части левой панели, а затем выберите **SQL Azure**.  
  
## <a name="options"></a>Параметры  
  
## <a name="connectivity"></a>Соединение  
**Интервал подтверждения**  
  
Задает интервал времени, используемый для механизма пульса для поддержки подключения SQL Azure в "минуты: секунды формат.  
  
**Значение по умолчанию**: "4:45 '  
  
Значение должно быть указано в меня: ss формат (например, "4:45 ' или ' 0:50 ').  
  
**Суффикс сервера SQL Azure**  
  
Указывает суффикс сервера SQL Azure  
  
**Значение по умолчанию**: «database.windows.net».  
  
