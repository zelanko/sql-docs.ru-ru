---
title: Перенос данных Access в SQL Server — база данных SQL Azure (Акцесстоскл) | Документация Майкрософт
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
ms.openlocfilehash: 8f0e93efee0c57c904c32ec52fbb560f973f21b8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67907143"
---
# <a name="migrating-access-data-into-sql-server---azure-sql-db-accesstosql"></a>Перенос данных доступа в SQL Server в базе данных SQL Azure (Акцесстоскл)
После успешного создания объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]можно выполнить перенос данных из Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure.  
  
## <a name="setting-migration-options"></a>Настройка параметров миграции  
Перед переносом данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure проверьте параметры миграции проекта в диалоговом окне " **Параметры проекта** ". В этом диалоговом окне можно задать размер пакета миграции, блокировку таблиц, проверку ограничений, срабатывание триггера вставки, обработку значений Identity и NULL, а также как обрабатывать даты, находящиеся вне [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] диапазона. Дополнительные сведения см. в разделе [Параметры проекта (миграция)](https://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d).  
  
## <a name="migrating-data"></a>Перенос данных  
Миграция данных — это операция групповой загрузки, которая перемещает строки данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в или SQL Azure в транзакциях. Число строк, загружаемых в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure в каждой транзакции, настраивается в параметрах проекта.  
  
Чтобы просмотреть сообщения миграции, убедитесь, что панель вывода видна. Если это не так, в меню **вид** выберите **выходные данные**.  
  
**Перенос данных**  
  
1.  Убедитесь, что объекты базы данных Access загружены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure.  
  
2.  В окне Обозреватель метаданных Access выберите объекты, содержащие данные, которые необходимо перенести.  
  
    -   Чтобы перенести данные для всей базы данных, установите флажок рядом с именем базы данных.  
  
    -   Чтобы перенести данные из отдельных таблиц, разверните базу данных, разверните узел **таблицы**, а затем установите флажок рядом с таблицей. Чтобы пропустить данные из отдельных таблиц, снимите флажок.  
  
3.  Щелкните правой кнопкой мыши элемент **базы данных** и выберите команду **перенести данные**.  
  
Вы также можете выполнить миграцию данных за пределами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SSMA с помощью программы командной строки [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **bcp** или. Дополнительные сведения об этих средствах см [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . в электронной документации по.  
  
## <a name="next-step"></a>Дальнейшее действие  
Если у вас есть доступ к приложениям базы данных, которые вы хотите продолжить использовать после миграции, свяжите таблицы базы данных Access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с таблицами или SQL Azure. Дополнительные сведения см. [в разделе Связывание приложений Access с SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md).  
  
## <a name="see-also"></a>См. также:  
[Миграция баз данных Access в SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Задание параметров преобразования и миграции](setting-conversion-and-migration-options-accesstosql.md)  
  
