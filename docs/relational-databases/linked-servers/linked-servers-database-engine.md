---
title: Связанные серверы (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 05/29/2019
ms.prod: sql
ms.technology: ''
ms.prod_service: database-engine
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB, linked servers
- OLE DB provider, linked servers
- server management [SQL Server], linked servers
- linked servers [SQL Server]
- distributed queries [SQL Server], linked servers
- servers [SQL Server], linked
- remote servers [SQL Server], linked servers
- linked servers [SQL Server], about linked servers
ms.assetid: 6ef578bf-8da7-46e0-88b5-e310fc908bb0
author: stevestein
ms.author: sstein
ms.openlocfilehash: a7dc1d67e45bb8d67cebff9deb3a694b09038154
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68073658"
---
# <a name="linked-servers-database-engine"></a>Связанные серверы (компонент Database Engine)

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Связанные серверы позволяют [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и [управляемым экземплярам Базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-index) вести чтение данных из удаленных источников данных и выполнять команды на удаленных серверах баз данных (например, источниках данных OLE DB) за пределами экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Обычно связанные серверы настроены на включение компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] для выполнения инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , включающей таблицы в другом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]или другом продукте для работы с базами данных, например Oracle. В качестве связанных серверов можно настроить источники данных OLE DB многих типов, в том числе [!INCLUDE[msCoName](../../includes/msconame-md.md)] Access, Excel и Azure CosmosDB.

> [!NOTE]
> Связанные серверы доступны в [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и управляемых экземплярах Базы данных SQL Azure. Они не включены в отдельную базу данных SQL Azure и эластичные пулы. Существуют некоторые ограничения для управляемых экземпляров, описание которых можно найти [здесь](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#linked-servers). 

## <a name="when-to-use-linked-servers"></a>Когда использовать связанные серверы?

  Связанные серверы позволяют реализовать распределенные базы данных, которые могут извлекать и обновлять данные в других базах данных. Они являются прекрасным решением в сценариях, где необходимо реализовать сегментирование баз данных без необходимости создания кода пользовательского приложения или прямой загрузки из удаленных источников данных. Концепция связанных серверов имеет следующие преимущества.  
  
-   Возможность доступа к данным за пределами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Возможность осуществлять распределенные запросы, обновления, команды и транзакции на разнородных источниках данных по всему предприятию.  
  
-   Возможность единообразной адресации разных источников данных.  
  
Можно настроить связанный сервер, используя инструкцию [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [sp_addlinkedserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) . Поставщики OLE DB существенно различаются по типу и количеству необходимых параметров. Например, некоторые поставщики требуют предоставления контекста безопасности для соединения с помощью [sp_addlinkedsrvlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md). Некоторые поставщики OLE DB разрешают использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для обновления данных в источнике данных OLE DB. Другие предоставляют доступ к данным только для чтения. Для информации о каждом поставщике OLE DB обратитесь к документации об этом поставщике OLE DB.  
  
## <a name="linked-server-components"></a>Компоненты связанных серверов  
 Определение связанного сервера задает следующие объекты.  
  
-   Поставщик OLE DB  
  
-   Источник данных OLE DB  
  
*Поставщиком OLE DB* является динамическая библиотека, осуществляющая управление и взаимодействие с определенными источниками данных. *Источник данных OLE DB* определяет конкретную базу данных, доступ к которой выполняется через интерфейс OLE DB. Хотя источники данных, запросы к которым выполняются с помощью определений связанных серверов, являются обычными базами данных, существуют поставщики OLE DB для разнообразных файлов и форматов файлов. Сюда входят текстовые файлы, данные электронных таблиц и результаты поиска полнотекстового содержимого.  
  
Поставщик OLE DB для собственного клиента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (PROGID: SQLNCLI11) является официальным поставщиком OLE DB для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предназначены для работы с поставщиком OLE DB, реализующим необходимые интерфейсы OLE DB. Однако работа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверялась только с поставщиком Native Client OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и некоторыми другими поставщиками.  
  
## <a name="linked-server-details"></a>Подробности настройки связанных серверов  
 На следующей иллюстрации показаны основы настройки связанных серверов.  
  
 ![Уровень клиента, уровень сервера и уровень сервера баз данных](../../relational-databases/linked-servers/media/lsvr.gif "Уровень клиента, уровень сервера и уровень сервера баз данных")  
  
Обычно связанные серверы используются для обработки распределенных запросов. Если клиентское приложение выполняет распределенный запрос через связанный сервер, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проводит синтаксический анализ команды и передает запросы поставщику OLE DB. Запрос на набор строк может быть в форме выполнения запроса к поставщику или в форме открытия базовой таблицы из поставщика.  
  
> [!NOTE]
> Чтобы источник данных мог вернуть данные при помощи связанного сервера, поставщик OLE DB (динамическая библиотека) для этого источника данных должен присутствовать на том же сервере, что и экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT] 
> При использовании поставщика OLE DB учетная запись, под которой выполняется служба сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], должна иметь разрешения на чтение и выполнение для каталога и всех его подкаталогов, в котором установлен поставщик. Сюда входят поставщики, выпущенные корпорацией Майкрософт, и любые сторонние поставщики. 
  
## <a name="managing-providers"></a>Управление поставщиками  
Имеется набор параметров, определяющих, как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] загружает и использует поставщики OLE DB, заданные в реестре.  
  
## <a name="managing-linked-server-definitions"></a>Управление определениями связанных серверов  
При установке связанного сервера зарегистрируйте параметры соединения и источника данных при помощи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. После регистрации к этому источнику данных можно обращаться по одному логическому имени.  
  
Для управления определениями связанного сервера можно использовать хранимые процедуры и представления каталога.  
  
-   Создайте определение связанного сервера, выполнив процедуру **sp_addlinkedserver**.  
  
-   Просмотрите сведения о связанных серверах, определенных в конкретном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выполнив запрос к представлениям системного каталога **sys.servers** .  
  
-   Удалите определение связанного сервера, выполнив процедуру **sp_dropserver**. Эта хранимая процедура может также использоваться для удаления удаленного сервера.  
  
Определять связанные серверы можно также в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. В обозревателе объектов щелкните правой кнопкой мыши **Объекты сервера**, выберите **Создать**и выберите **Связанный сервер**. Определение связанного сервера можно удалить, щелкнув правой кнопкой мыши имя связанного сервера и выбрав **Удалить**.  
  
 При выполнении распределенного запроса к связанному серверу необходимо указать полное, состоящее из четырех частей имя таблицы для каждого источника данных, к которому выполняется запрос. Это четырехкомпонентное имя должно быть в форме _linked\_server\_name.catalog_ **.** _schema_ **.** _object\_name_.  
  
> [!NOTE]  
> Связанные серверы могут быть определены таким образом, чтобы указывать на сервер, на котором они определены (обратная связь). Серверы с обратной связью наиболее полезны для тестирования приложения, в котором используются распределенные запросы в односерверной сети. Серверы, связанные с помощью петлевого адреса, предназначены для тестирования и не поддерживаются во многих операциях, таких как распределенные транзакции.  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Создание связанных серверов (компонент SQL Server Database Engine)](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md)  
  
 [sp_addlinkedserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)  
  
 [sp_addlinkedsrvlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)  
  
 [sp_dropserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)  
  
## <a name="related-content"></a>См. также  
 [sys.servers (Transact-SQL)](../../relational-databases/system-catalog-views/sys-servers-transact-sql.md)  
  
 [sp_linkedservers (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)  
  
  
