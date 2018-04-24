---
title: Скрипт SQL адресной книги | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: 409b3f8b-0ced-4867-acbe-b245dcdf6702
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6d4e84958860f790254319e8d23b0720e22a710c
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="running-the-address-book-sql-script"></a>Скрипт SQL адресной книги
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Необходимо использовать служебную программу командной строки ISQL/Query Analyzer или SQL Server Enterprise Manager, чтобы запуск включены скрипт SQL (Sampleemp.sql), в котором:  
  
-   Создает новую базу данных, AddrBookDB, на устройство по умолчанию.  
  
-   Подключается к базе данных AddrBookDB.  
  
-   Создает таблицу Employee.  
  
-   Заполняет эту таблицу с образцами данных.  
  
-   Выполняется простой инструкции SELECT, чтобы проверить заполнение таблицы базы данных.  
  
-   Настраивает учетную запись пользователя, называется «adcdemo» с паролем «adcdemo».  
  
#### <a name="to-run-the-sampleempsql-script-in-microsoft-sql-server-65"></a>Для выполнения сценария Sampleemp.sql в Microsoft SQL Server 6.5  
  
1.  Нажмите кнопку **запустить**, пункты **программы**, а затем **Microsoft SQL Server 6.5**. Нажмите кнопку **SQL Enterprise Manager**.  
  
2.  Из **средства** меню, нажмите кнопку **средства запросов SQL**.  
  
3.  Нажмите кнопку **загрузки скрипта SQL** и перейдите к c:\Platform SDK\Samples\DataAccess\RDS\AddressBook.  
  
4.  Выберите файл Sampleemp.sql. Нажмите кнопку **Открыть**.  
  
5.  Нажмите кнопку **выполнить запрос** кнопки (зеленая стрелка на панели инструментов).  
  
6.  После его выполнения, закройте **запроса** и **Enterprise Manager** windows.  
  
#### <a name="to-run-the-sampleempsql-script-in-microsoft-sql-server-70"></a>Для выполнения сценария Sampleemp.sql в Microsoft SQL Server 7.0  
  
1.  Нажмите кнопку **запустить**, пункты **программы**, а затем **Microsoft SQL Server 7.0**. Нажмите кнопку **Enterprise Manager**.  
  
2.  Убедитесь, что SQL Server, который вы хотите использовать выбран в списке зарегистрированных серверов в Enterprise Manager.  
  
3.  Из **средства** меню, нажмите кнопку **SQL Server Query Analyzer**.  
  
4.  Нажмите кнопку **загрузки скрипта SQL** кнопки (откройте папку на панели инструментов) и перейдите к c:\Platform SDK\Samples\DataAccess\RDS\AddressBook.  
  
5.  Выберите файл Sampleemp.sql. Нажмите кнопку **Открыть**.  
  
6.  Нажмите кнопку **выполнить запрос** кнопки (зеленая стрелка на панели инструментов) или **F5**.  
  
7.  После его выполнения, закройте **запроса**, **Query Analyzer**, и **Enterprise Manager** windows.  
  
## <a name="see-also"></a>См. также  
 [Выполнение примера приложения адресной книги](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)


