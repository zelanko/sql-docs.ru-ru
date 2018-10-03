---
title: Миграция данных Access в SQL Server — база данных Azure SQL (AccessToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- bulk loading data
- data, loading into SQL Azure
- data, loading into SQL Server
- migrating databases, loading data
- migrating databases, options
- options, migrating data
- SQL Azure, migrating data into
- SQL Server, migrating data into
ms.assetid: f3b18af7-1af0-499d-a00d-a0af94895625
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: ab3ce18b1b79951c76b34be3f90b2d8782ba64e4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773831"
---
# <a name="migrating-access-data-into-sql-server---azure-sql-db-accesstosql"></a>Миграция данных Access в SQL Server — база данных Azure SQL (AccessToSQL)
После успешного создания объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], можно перенести данные с доступом к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure.  
  
## <a name="setting-migration-options"></a>Настройка параметров миграции  
Чтобы перенести данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, проверьте параметры проекта миграции в **параметры проекта** диалоговое окно. В этом диалоговом окне можно задать размер пакета миграции, блокировка таблицы, проверки, вставки выполнения триггеров, идентификации и обработки, значение null и как обрабатывать даты из ограничений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] диапазона. Дополнительные сведения см. в разделе [параметры проекта (миграция)](http://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d).  
  
## <a name="migrating-data"></a>Перенос данных  
Перенос данных является операцией массовой загрузки, которая перемещает строки данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure в транзакциях. Число строк, загружаемых в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure в каждой транзакции настраивается в параметрах проекта.  
  
Чтобы просмотреть сообщения миграции, убедитесь, что отображается на панели вывода. Если это не так, на **представление** меню, выберите **вывода**.  
  
**Для переноса данных**  
  
1.  Убедитесь, что вы загрузили объектов базы данных Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure.  
  
2.  Выберите объекты, которые содержат данные, которые требуется перенести в обозревателе метаданных доступа:  
  
    -   Для переноса данных для всей базы данных, установите флажок рядом с именем базы данных.  
  
    -   Чтобы перенести данные из отдельных таблиц, разверните базу данных, разверните узел **таблиц**, а затем установите флажок рядом с таблицей. Чтобы исключить данные из отдельных таблиц, снимите флажок.  
  
3.  Щелкните правой кнопкой мыши **баз данных** , а затем выберите **переноса данных**.  
  
Данные за пределами SSMA можно перенести с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **bcp** программы командной строки или [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Дополнительные сведения об этих средствах см. в разделе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.  
  
## <a name="next-step"></a>Следующий шаг  
При наличии приложений базы данных Access, которые вы хотите продолжать использовать после миграции, свяжите таблицы базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или таблиц SQL Azure. Дополнительные сведения см. в разделе [связывания приложения Access в SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md).  
  
## <a name="see-also"></a>См. также  
[Миграция баз данных Access в SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Параметр преобразования и варианты миграции](setting-conversion-and-migration-options-accesstosql.md)  
  
