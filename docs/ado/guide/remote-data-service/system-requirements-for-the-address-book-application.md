---
description: Требования к системе для приложения адресной книги
title: Требования к системе для приложения адресной книги | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: da385405-1c9a-478b-9bf6-fba70015324c
author: rothja
ms.author: jroth
ms.openlocfilehash: 7edd6f3c383c1563122bff053e39a372dff264b3
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91722836"
---
# <a name="system-requirements-for-the-address-book-application"></a>Требования к системе для приложения адресной книги
Чтобы настроить пример приложения адресной книги, необходимо обеспечить соответствие следующим требованиям к программному обеспечению и базе данных:  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](/dotnet/framework/wcf/).  
  
## <a name="software-requirements"></a>Требования к программному обеспечению  
 Для запуска этого веб-приложения серверные требования к программному обеспечению включают:  
  
-   Microsoft Windows NT® Server 4,0 с пакетом обновления 3 (SP3) или более поздней версии или Microsoft Windows® 2000 Server.  
  
-   Microsoft службы IIS (IIS) версии 3,0 или более поздней, со Active Server страницами.  
  
 Требования к программному обеспечению клиентского компьютера для запуска этого веб-приложения включают:  
  
-   Microsoft Internet Explorer 4,0 или более поздней версии.  
  
-   Microsoft Windows NT 4,0 Workstation или Server, Windows 2000 или Microsoft Windows 98.  
  
## <a name="database-requirements"></a>Требования к базе данных  
 Для использования этого образца необходимо следующее:  
  
-   Сервер базы данных Microsoft® SQL Server версии 6,5 или более поздней.  
  
-   Привилегии для создания базы данных и заполнения ее образцом данных.  
  
-   Проверка заполненных данных с помощью программы Enterprise Manager или ISQL (которая называется анализатором запросов в SQL Server 7,0).  
  
 Если у вас нет прав, администратору базы данных может потребоваться настроить систему и предоставить вам разрешение на доступ к базе данных или настроить базу данных.  
  
## <a name="see-also"></a>См. также  
 [Выполнение скрипта SQL адресной книги](./running-the-address-book-sql-script.md)   
 [Объект элемента управления (RDS)](../../reference/rds-api/datacontrol-object-rds.md)   
 [Выполнение примера приложения адресной книги](./running-the-address-book-sample-application.md)