---
title: Сопоставление схем DB2 с SQL Server схемами (DB2ToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 05ff7bd4-e60b-4f48-a893-bc2346aa9a8a
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 50845a9bdf3c3185d7b69bb86a75b2a3d332ef6b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68074177"
---
# <a name="mapping-db2-schemas-to-sql-server-schemas-db2tosql"></a>Сопоставление схем DB2 с SQL Server схемами (DB2ToSQL)
В DB2 каждая база данных имеет одну или несколько схем. По умолчанию SSMA переносит все объекты в схеме DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных, указанную для схемы. Однако можно настроить сопоставление между схемами DB2 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базами данных.  
  
## <a name="db2-and-sql-server-schemas"></a>Схемы DB2 и SQL Server  
База данных DB2 содержит схемы. Экземпляр служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит несколько баз данных, каждый из которых может иметь несколько схем.  
  
Концепция DB2 схемы сопоставляется с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] концепцией базы данных и одной из ее схем. Например, DB2 может иметь схему с именем **HR**. Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может иметь базу данных с именем **HR**, а в этой базе данных — схемы. Одной из схем является схема **dbo** (или владелец базы данных). По умолчанию схема DB2 **HR** будет сопоставлена с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базой данных и схемой **HR. dbo**. SSMA ссылается на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сочетание базы данных и схемы в качестве схемы.  
  
Сопоставление между DB2 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемами можно изменить.  
  
## <a name="modifying-the-target-database-and-schema"></a>Изменение целевой базы данных и схемы  
В SSMA можно сопоставлять схему DB2 с любой доступной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемой.  
  
**Изменение базы данных и схемы**  
  
1.  В обозревателе метаданных DB2 выберите **схемы**.  
  
    Вкладка **сопоставление схем** доступна также при выборе отдельной базы данных, папки **Schemas** или отдельных схем. Список на вкладке **сопоставление схемы** настроен для выбранного объекта.  
  
2.  На панели справа перейдите на вкладку **сопоставление схем** .  
  
    Вы увидите список всех схем DB2, за которыми следует целевое значение. Этот целевой объект обозначается в нотации с двумя частями (*Database. Schema*), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] где объекты и данные будут перенесены.  
  
3.  Выберите строку, содержащую сопоставление, которое необходимо изменить, и нажмите кнопку **изменить**.  
  
    В диалоговом окне **Выбор целевой схемы** можно просмотреть доступную целевую базу данных и схему или ввести имя базы данных и схемы в текстовое поле в нотации с двумя частями (Database. Schema), а затем нажать кнопку **ОК**.  
  
4.  Целевое изменение на вкладке **сопоставление схемы** .  
  
**Режимы сопоставления**  
  
-   Сопоставление с SQL Server  
  
Базу данных источника можно сопоставлять с любой целевой базой данных. По умолчанию база данных-источник сопоставляется с целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базой данных, к которой вы подключены с помощью SSMA. Если сопоставляемая Целевая база данных не является существующей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], будет выведено сообщение **"база данных и (или) схема не существует в целевых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] метаданных. Он будет создан во время синхронизации. Вы хотите продолжить?»** Нажмите кнопку "Да". Аналогичным образом можно сопоставлять схему с несуществующей схемой в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базе данных, которая будет создана во время синхронизации.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Возврат к базе данных и схеме по умолчанию  
Если вы настраиваете сопоставление между схемой DB2 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемой, можно вернуть сопоставление к значениям по умолчанию.  
  
**Возврат к базе данных и схеме по умолчанию**  
  
1.  На вкладке Сопоставление схемы выберите любую строку и нажмите кнопку **восстановить значения по умолчанию** , чтобы вернуться к базе данных и схеме по умолчанию.  
  
## <a name="next-steps"></a>Дальнейшие действия  
Если требуется проанализировать преобразование объектов DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объекты, можно использовать [отчет о переносе данных (SSMA Common)](https://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241).  
  
## <a name="see-also"></a>См. также:  
[Подключение к SQL Server &#40;DB2eToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md)  
[Перенос баз данных DB2 в SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
