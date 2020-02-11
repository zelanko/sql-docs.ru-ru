---
title: Реализация пользовательского арбитра конфликтов для статьи публикации слиянием | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], stored procedure-based resolvers
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 76bd8524-ebc1-4d80-b5a2-4169944d6ac0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 47d0f7c4eb6c78b9e551fafdc1e018a27604086e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62721230"
---
# <a name="implement-a-custom-conflict-resolver-for-a-merge-article"></a>Реализация пользовательского арбитра конфликтов для статьи публикации слиянием
  В данном разделе описывается реализация пользовательского арбитра конфликтов для статьи публикации слиянием в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] или [Пользовательского арбитра конфликтов на основе COM](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md).  
  
 **В этом разделе**  
  
-   **Для реализации пользовательского сопоставителя конфликтов для статьи публикации слиянием используется:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Сопоставитель на основе COM](#COM)  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Собственный пользовательский арбитр конфликтов можно записать в виде хранимой процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)] на каждом издателе. Во время синхронизации эта хранимая процедура вызывается при возникновении конфликтов в статье, для которой был зарегистрирован сопоставитель, и данные о строке с конфликтом передаются агентом слияния в необходимые параметры этой процедуры. Пользовательские сопоставители конфликтов на основе хранимых процедур всегда создаются на издателе.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разрешения на хранимые процедуры вызываются только для обработки конфликтов на основе изменений строк. Их нельзя использовать для обработки других типов конфликтов, таких как ошибки вставки, возникшие из-за нарушения ограничений PRIMARY KEY или ограничений уникального индекса.  
  
#### <a name="to-create-a-stored-procedure-based-custom-conflict-resolver"></a>Создание пользовательского сопоставителя конфликтов на основе хранимых процедур  
  
1.  На издателе в базе данных публикации или **msdb** создайте новую системную хранимую процедуру, реализующую следующие обязательные параметры.  
  
    |Параметр|Тип данных|Description|  
    |---------------|---------------|-----------------|  
    |**@tableowner**|`sysname`|Имя владельца таблицы, в которой разрешается конфликт. Это владелец таблицы в базе данных публикации.|  
    |**@tablename**|`sysname`|Имя таблицы, в которой разрешается конфликт.|  
    |**@rowguid**|`uniqueidentifier`|Уникальный идентификатор строки конфликта.|  
    |**@subscriber**|`sysname`|Имя сервера, с которого распространяется вызвавшее конфликт изменение.|  
    |**@subscriber_db**|`sysname`|Имя базы данных, из которой распространяется вызвавшее конфликт изменение.|  
    |**@log_conflictПРОВЕРКИ**|`int`|Определяет, должен ли процесс слияния зарегистрировать конфликт для последующего разрешения.<br /><br /> **0** = не записывать в журнал конфликт.<br /><br /> **1** = конфликт проигравший для подписчика.<br /><br /> **2** = издатель проигравший.|  
    |**@conflict_messageПРОВЕРКИ**|`nvarchar(512)`|Сообщения, которые должны быть выданы о разрешении конфликта, если конфликт был зарегистрирован.|  
    |**@destowner**|`sysname`|Владелец опубликованной таблицы на подписчике.|  
  
     Эта хранимая процедура использует значения, переданные агентом слияния этим параметрам для применения пользовательской логики устранения конфликтов. Она должна вернуть результирующий набор, содержащий одну строку, соответствующий структуре базовой таблицы и содержащий значения данных для приоритетной версии строки.  
  
2.  Предоставьте разрешения EXECUTE на хранимую процедуру любым именам входа, используемым подписчиками для соединения с издателем.  
  
#### <a name="to-use-a-custom-conflict-resolver-with-a-new-table-article"></a>Использование нестандартного сопоставителя конфликтов с новой статьей таблицы  
  
1.  Выполните хранимую процедуру [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) , чтобы определить статью. При этом укажите значение **MicrosoftSQL** **Server Stored Procedure Resolver** в параметре **@article_resolver** и имя хранимой процедуры, реализующей логику сопоставителя конфликтов в параметре **@resolver_info** . Дополнительные сведения см. в статье [определить статью](publish/define-an-article.md).  
  
#### <a name="to-use-a-custom-conflict-resolver-with-an-existing-table-article"></a>Использование нестандартного сопоставителя конфликтов с существующей статьей таблицы  
  
1.  Выполните [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), указав **@publication**, **@article**, значение **article_resolver** **@property**в параметре и значение **MicrosoftSQL** **Server stored процедурересолвер** для **@value**.  
  
2.  Выполните [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), указав **@publication**, **@article**, значение **resolver_info** **@property**в параметре и имя хранимой процедуры, которая реализует логику сопоставителя конфликтов для **@value**.  
  
##  <a name="COM"></a>Использование пользовательского арбитра конфликтов на основе COM  
 Пространство имен <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> реализует интерфейс, позволяющий писать сложную бизнес-логику для обработки событий и разрешения конфликтов, происходящих во время синхронизации репликации слиянием. Дополнительные сведения см. в [статье реализация обработчика бизнес-логики для статьи публикации слиянием](implement-a-business-logic-handler-for-a-merge-article.md). Для разрешения конфликтов можно записать в машинном коде собственную бизнес-логику. Эта логика построена как COM-компонент и компилируется в динамические библиотеки (DLL) с помощью таких продуктов, как [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C++. Такой пользовательский сопоставитель конфликтов на основе COM должен реализовывать интерфейс **ICustomResolver** , разработанный специально для разрешения конфликтов.  
  
#### <a name="to-create-and-register-a-com-based-custom-conflict-resolver"></a>Создание и регистрация пользовательского сопоставителя конфликтов на основе COM  
  
1.  В COM-совместимой среде разработчика добавьте ссылки на библиотеку пользовательского сопоставителя.  
  
2.  В проекте Visual C++ используйте директиву #import для импорта этой библиотеки.  
  
3.  Создайте класс, реализующий интерфейс **ICustomResolver** .  
  
4.  Обеспечьте выполнение соответствующих методов и свойств.  
  
5.  Постройте проект, создающий файл библиотеки пользовательского сопоставителя.  
  
6.  Разверните эту библиотеку в каталоге, содержащем исполняемый файл агента слияния (обычно «\Microsoft SQL Server\100\COM»).  
  
    > [!NOTE]  
    >  Пользовательский сопоставитель конфликтов необходимо развернуть на подписчике для подписки по запросу, на распространителе для принудительной подписки или на веб-сервере, который используется для веб-синхронизации.  
  
7.  Зарегистрируйте библиотеку пользовательского сопоставителя конфликтов с помощью программы regsvr32.exe из каталога развертывания следующим образом.  
  
    ```  
    regsvr32.exe mycustomresolver.dll  
    ```  
  
8.  На издателе выполните хранимую процедуру [sp_enumcustomresolvers (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql), чтобы проверить, не зарегистрирована ли уже эта библиотека в качестве пользовательского арбитра конфликтов.  
  
9. Чтобы зарегистрировать библиотеку в качестве пользовательского сопоставителя конфликтов, выполните [sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql)на распространителе. Укажите понятное имя COM-объекта **@article_resolver**для, идентификатор библиотеки (CLSID) для **@resolver_clsid**и значение `false` для. **@is_dotnet_assembly**  
  
    > [!NOTE]  
    >  Если пользовательский арбитр конфликтов больше не нужен, вы можете отменить его регистрацию с помощью хранимой процедуры [sp_unregistercustomresolver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql).  
  
10. В кластере повторите шаги 5-8, чтобы зарегистрировать пользовательский сопоставитель на всех узлах кластера (необязательно). Это нужно для того, чтобы пользовательский сопоставитель смог правильно загрузить посредник после отработки отказа.  
  
#### <a name="to-use-a-custom-conflict-resolver-with-a-new-table-article"></a>Использование нестандартного сопоставителя конфликтов с новой статьей таблицы  
  
1.  На издателе выполните [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) и обратите внимание на понятное имя нужного распознавателя.  
  
2.  Чтобы определить статью, в базе данных публикации издателя выполните процедуру [sp_addmergearticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Укажите понятное имя арбитра статей из шага 1 в параметре **@article_resolver**. Дополнительные сведения см. в статье [определить статью](publish/define-an-article.md).  
  
#### <a name="to-use-a-custom-conflict-resolver-with-an-existing-table-article"></a>Использование нестандартного сопоставителя конфликтов с существующей статьей таблицы  
  
1.  На издателе выполните [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) и обратите внимание на понятное имя нужного распознавателя.  
  
2.  Выполните [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), указав **@publication**, **@article**, значение **article_resolver** **@property**в параметре и понятное имя арбитра статей из шага 1 в параметре **@value**.  
  
#### <a name="viewing-a-sample-custom-resolver"></a>Просмотр образца пользовательского сопоставителя  
  
1.  Пример доступен в образцах файлов SQL Server 2000. Скачайте файл [**файл sql2000samples. zip**](https://github.com/Microsoft/sql-server-samples/blob/master/samples/tutorials/Miscellaneous/sql2000samples.zip). Это позволит загрузить 3 файла, объем которых составляет 6,9 МБ.  
  
2.  Извлеките файлы из загруженного сжатого CAB-файла.  
  
3.  Запустите **файл Setup. exe.**  
  
    > [!NOTE]  
    >  При выборе параметров установки необходимо установить только образцы **Репликации** . (Путь установки по умолчанию — **C:\Program Files (x86) \Microsoft SQL Server\\2000 Samples\1033**)  
  
4.  Перейдите в папку установки. (По умолчанию используется папка **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\sqlrepl\unzip_sqlreplSP3.exe**)  
  
5.  Выполните программу **unzip_sqlreplSP3.exe** .  
  
    > [!NOTE]  
    >  Пример сопоставителя com будет установлен (по умолчанию) в папку **C:\Program Files (x86) \Microsoft SQL Server 2000 Samples\1033\sqlrepl\resolver\subspres** .  
  
6.  В папке **subspres** найдите все вхождения **#include sqlres.h** во всех исходных файлах и замените их значением **#import "replrec.dll" no_namespace, raw_interfaces_only**  
  
## <a name="see-also"></a>См. также:  
 [Расширенное обнаружение и разрешение конфликтов при репликации слиянием](merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Пользовательские арбитры конфликтов на основе COM](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md)   
 [Рекомендации по обеспечению безопасности репликации](security/replication-security-best-practices.md)  
  
  
