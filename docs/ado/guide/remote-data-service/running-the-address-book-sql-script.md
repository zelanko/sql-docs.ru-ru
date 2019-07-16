---
title: Запуск сценария SQL адресной книги | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: 409b3f8b-0ced-4867-acbe-b245dcdf6702
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5adc631a3c3f7a66c02f9ebfe541fa5e923deb0a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67922232"
---
# <a name="running-the-address-book-sql-script"></a>Запуск сценария SQL адресной книги
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Необходимо использовать программу командной строки ISQL/Query Analyzer или SQL Server Enterprise Manager, чтобы запустить включен сценарий SQL (Sampleemp.sql):  
  
-   Создает новую базу данных, AddrBookDB, на устройство по умолчанию.  
  
-   Подключается к базе данных, AddrBookDB.  
  
-   Создает таблицу Employee.  
  
-   Заполняет таблицу с образцами данных.  
  
-   Выполняется простой инструкции SELECT, чтобы проверить заполнение таблицы базы данных.  
  
-   Настройка учетной записи с именем «adcdemo» с паролем «adcdemo.»  
  
#### <a name="to-run-the-sampleempsql-script-in-microsoft-sql-server-65"></a>Для выполнения сценария Sampleemp.sql в Microsoft SQL Server 6.5  
  
1.  Нажмите кнопку **запустить**, пункты **программы**и выберите команду **Microsoft SQL Server 6.5**. Нажмите кнопку **SQL Enterprise Manager**.  
  
2.  Из **средства** меню, щелкните **средство запроса SQL**.  
  
3.  Нажмите кнопку **скрипт SQL нагрузки** и перейдите к c:\Platform SDK\Samples\DataAccess\RDS\AddressBook.  
  
4.  Выберите файл Sampleemp.sql. Нажмите кнопку **Открыть**.  
  
5.  Нажмите кнопку **выполнить запрос** кнопки (зеленую стрелку на панели инструментов).  
  
6.  После его выполнения, закройте **запроса** и **Enterprise Manager** windows.  
  
#### <a name="to-run-the-sampleempsql-script-in-microsoft-sql-server-70"></a>Для выполнения сценария Sampleemp.sql в Microsoft SQL Server 7.0  
  
1.  Нажмите кнопку **запустить**, пункты **программы**и выберите команду **Microsoft SQL Server 7.0**. Нажмите кнопку **Enterprise Manager**.  
  
2.  Убедитесь, что в списке зарегистрированных серверов в Enterprise Manager установлен SQL Server, который вы хотите использовать.  
  
3.  Из **средства** меню, щелкните **SQL Server Query Analyzer**.  
  
4.  Нажмите кнопку **скрипт SQL нагрузки** кнопки (открыть папку на панели инструментов) и перейдите к c:\Platform SDK\Samples\DataAccess\RDS\AddressBook.  
  
5.  Выберите файл Sampleemp.sql. Нажмите кнопку **Открыть**.  
  
6.  Нажмите кнопку **выполнить запрос** кнопки (зеленую стрелку на панели инструментов) или **F5**.  
  
7.  После его выполнения, закройте **запроса**, **Query Analyzer**, и **Enterprise Manager** windows.  
  
## <a name="see-also"></a>См. также  
 [Выполнение примера приложения адресной книги](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)


