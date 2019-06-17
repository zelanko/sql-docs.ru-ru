---
title: Запуск и остановка набора элементов сбора | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- collection sets [SQL Server], stopping
- collection sets [SQL Server], starting
ms.assetid: 48a7b2fe-6bc3-4278-a7ec-1babc1290345
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 96f5a873e8d172254e1ea18abbd0c570b27a35ed
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62918467"
---
# <a name="start-or-stop-a-collection-set"></a>Запуск или остановка набора элементов сбора
  В этом разделе описывается запуск и остановка набора элементов сбора в среде [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Предварительные требования](#Prerequisites)  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Запуск и остановка набора элементов сбора с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Хранимые процедуры и представления каталога сборщика данных хранятся в базе данных **msdb** .  
  
-   В отличие от обычных хранимых процедур, параметры хранимых процедур для сборщика данных жестко типизированы и не поддерживают автоматическое преобразование типов данных. Если эти параметры не вызываются вместе с правильными типами данных входных параметров, как указано в описании аргумента, хранимая процедура возвращает ошибку.  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Должен быть запущен агент SQL Server.  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Для получения информации о наборах элементов сбора запросите представление каталога [syscollector_collection_sets](/sql/relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql) .  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется членство в предопределенной роли базы данных **dc_operator** . Если набор элементов сбора не имеет учетной записи-посредника, требуется членство в предопределенной роли сервера **sysadmin** . Примеры  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-start-a-collection-set"></a>Запуск набора сбора  
  
1.  В обозревателе объектов разверните узел **Управление** , затем узел **Сбор данных**и узел **Наборы элементов сбора системных данных**.  
  
2.  Щелкните правой кнопкой мыши необходимый для запуска набор сбора и выберите команду **Запустить набор сбора данных**.  
  
     Результат этого действия выводится в окне, а зеленая стрелка на значке набора сбора означает его запуск.  
  
#### <a name="to-stop-a-collection-set"></a>Остановка набора элементов сбора:  
  
1.  В обозревателе объектов разверните узел **Управление** , затем узел **Сбор данных**и узел **Наборы элементов сбора системных данных**.  
  
2.  Щелкните правой кнопкой мыши набор элементов сбора, который необходимо остановить, и выберите команду **Остановить набор сбора данных**.  
  
     Результат этого действия выводится в окне, а красный круг на значке набора сбора означает его остановку.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-start-a-collection-set"></a>Запуск набора сбора  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере используется процедура [sp_syscollector_start_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql) для запуска набора элементов сбора с идентификатором `1`.  
  
```sql  
USE msdb;  
GO  
EXEC sp_syscollector_start_collection_set @collection_set_id = 1;  
```  
  
#### <a name="to-stop-a-collection-set"></a>Остановка набора элементов сбора:  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере используется процедура [sp_syscollector_stop_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql) для остановки набора элементов сбора с идентификатором `1`.  
  
```sql  
USE msdb;  
GO  
EXEC sp_syscollector_stop_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>См. также  
 [Представления сборщика данных (Transact-SQL)](/sql/relational-databases/system-catalog-views/data-collector-views-transact-sql)   
 [Сбор данных](data-collection.md)  
  
  
