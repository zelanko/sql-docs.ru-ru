---
title: Требования к системе для адреса забронировать приложения | Документация Майкрософт
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
ms.assetid: da385405-1c9a-478b-9bf6-fba70015324c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2450cc97229a6629d4c2895f3960e3033d129789
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67922038"
---
# <a name="system-requirements-for-the-address-book-application"></a>Требования к системе для приложения адресной книги
Чтобы настроить пример приложения адресной книги, необходимо соответствовать следующим требованиям программного обеспечения и базы данных:  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="software-requirements"></a>Требования к программному обеспечению  
 Требования к программному обеспечению сервера компьютер для запуска этого веб-приложения включают:  
  
-   Microsoft Windows NT® Server 4.0 с пакетом обновления 3 или более поздней версии, или Microsoft Windows® 2000 Server.  
  
-   Microsoft Internet Information Services (IIS) версии 3.0 или более поздней версии, с ASP-страницы.  
  
 Требования к программному обеспечению клиента компьютера для запуска этого веб-приложения включают:  
  
-   Microsoft Internet Explorer 4.0 или более поздней версии.  
  
-   Microsoft Windows NT 4.0 Workstation или Server, Windows 2000 или Microsoft Windows 98.  
  
## <a name="database-requirements"></a>Требования к базе данных  
 Чтобы использовать этот пример, необходимо иметь:  
  
-   Сервер базы данных оперативной Microsoft® SQL Server 6.5 или более поздней версии.  
  
-   Привилегии, чтобы создать базу данных и заполнить его с использованием образца данных.  
  
-   Проверка заполненных данным с помощью Enterprise Manager или служебные программы ISQL (вызываемой Query Analyzer в SQL Server 7.0).  
  
 Если у вас нет прав, администратору базы данных может потребоваться настройка системы и дать разрешение в базу данных, или установить базу данных для вас.  
  
## <a name="see-also"></a>См. также  
 [Запуск сценария SQL адресной книги](../../../ado/guide/remote-data-service/running-the-address-book-sql-script.md)   
 [Объект DataControl (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Выполнение примера приложения адресной книги](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)


