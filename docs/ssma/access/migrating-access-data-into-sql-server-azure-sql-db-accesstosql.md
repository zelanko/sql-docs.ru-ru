---
title: Миграция данных Access в SQL Server — база данных Azure SQL (AccessToSQL) | Документация Майкрософт
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
caps.latest.revision: 17
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 9cb790ec1b79827b7db578001633c75ef6e1b191
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979476"
---
# <a name="migrating-access-data-into-sql-server---azure-sql-db-accesstosql"></a>Миграция данных Access в SQL Server — база данных Azure SQL (AccessToSQL)
После успешного создания объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], можно перенести данные с доступом к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure.  
  
## <a name="setting-migration-options"></a>Настройка параметров миграции  
Чтобы перенести данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, проверьте параметры проекта миграции в **параметры проекта** диалоговое окно. В этом диалоговом окне можно задать размер пакета миграции, блокировка таблицы, проверки, вставки выполнения триггеров, идентификации и обработки, значение null и как обрабатывать даты из ограничений [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] диапазона. Дополнительные сведения см. в разделе [параметры проекта (миграция)](http://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d).  
  
## <a name="migrating-data"></a>Перенос данных  
Перенос данных является операцией массовой загрузки, которая перемещает строки данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure в транзакциях. Число строк, загружаемых в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure в каждой транзакции настраивается в параметрах проекта.  
  
Чтобы просмотреть сообщения миграции, убедитесь, что отображается на панели вывода. Если это не так, на **представление** меню, выберите **вывода**.  
  
**Для переноса данных**  
  
1.  Убедитесь, что вы загрузили объектов базы данных Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure.  
  
2.  Выберите объекты, которые содержат данные, которые требуется перенести в обозревателе метаданных доступа:  
  
    -   Для переноса данных для всей базы данных, установите флажок рядом с именем базы данных.  
  
    -   Чтобы перенести данные из отдельных таблиц, разверните базу данных, разверните узел **таблиц**, а затем установите флажок рядом с таблицей. Чтобы исключить данные из отдельных таблиц, снимите флажок.  
  
3.  Щелкните правой кнопкой мыши **баз данных** , а затем выберите **переноса данных**.  
  
Данные за пределами SSMA можно перенести с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **bcp** программы командной строки или [!INCLUDE[ssISnoversion](../../includes/ssisnoversion_md.md)]. Дополнительные сведения об этих средствах см. в разделе [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Books Online.  
  
## <a name="next-step"></a>Следующий шаг  
При наличии приложений базы данных Access, которые вы хотите продолжать использовать после миграции, свяжите таблицы базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или таблиц SQL Azure. Дополнительные сведения см. в разделе [связывания приложения Access в SQL Server](http://msdn.microsoft.com/82374ad2-7737-4164-a489-13261ba393d4).  
  
## <a name="see-also"></a>См. также  
[Миграция баз данных Access в SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[Параметр преобразования и варианты миграции](http://msdn.microsoft.com/0a7304df-2f35-4453-96ef-7ac83dea1167)  
  
