---
title: "Сценарии служб удаленных рабочих СТОЛОВ | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: a7dcad87-aaf0-4b02-9660-472f8469761c
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 920df727d2714629a45280133c53011afccc5c4d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="rds-scenario"></a>Сценарии служб удаленных рабочих СТОЛОВ
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Адресная книга приложения представляет собой сценарий, показано, как использовать удаленной службе данных (RDS) для создания простого и данными веб-приложения — online корпоративной адресной книги. Этот сценарий полезен для Microsoft Visual Basic Scripting Edition (VBScript) и программистов COM, которые необходимо освоить использование ActiveX элементы управления данными с помощью служб удаленных рабочих СТОЛОВ и для программного обеспечения более опытным разработчикам, желающим построения веб-приложений, ориентированных на данные.  
  
 Этот сценарий предполагает, что вы знаете, как использовать основные теги разметки HTML, методы привязки данных используйте DHTML и программы с элементами управления ActiveX.  
  
 После установки пакета SDK в каталоге SDK на samples\dataaccess\rds\AddressBook\AddressBook.asp можно найти полный исходный код для примера приложения адресной книги. Чтобы просмотреть сценарий адресную книгу, введите в Internet Explorer 4.0 или более поздней версии,  **http://*веб-сервере*/RDS/AddressBook/AddressBook.asp** где *веб-сервере* имя присвоенное Windows NT 4.0 или Windows 2000, веб-сервере, на котором работает сервер Internet Information Services (IIS) и ASP.  
  
## <a name="introduction-to-address-book"></a>Введение в адресную книгу  
 Образец приложения адресная книга предоставляет простой online адресной книги, можно использовать для публикации каталога с возможностью поиска через интрасеть. Адресная книга разработан таким образом, пользователь может вводить строку поиска в одно или несколько полей для запроса сведений о сотрудниках. Чтобы показать основные возможности удаленной службы данных, пример приложения намеренно хранится на небольшой минимальное число объектов и полей.  
  
 Интерфейс приложения состоит из следующих частей:  
  
-   Без визуального **RDS. DataControl** объекта привязки к данным, используемый клиентом для подключения к базе данных.  
  
-   Критерии поиска HTML текстовые поля, которые действуют как поля ввода для атрибута сотрудника.  
  
-   Кнопки HTML для создания запросов, снимите полей, обновить базу данных со сведениями о сотрудниках, отменить ожидающие изменения и перемещаться строки данных, отображаемых в сетке.  
  
-   DHTML привязки данных для отображения данных возвращаемый запросами к серверной базе данных (через **RDS. DataControl** объекта привязки к данным) в таблице.  
  
-   VBScript подпрограммы, которые подключения каждого из элементов, которые было указано выше и разрешить им взаимодействовать. Также код VBScript используется для инициализации **RDS. DataControl** объекта и динамически создавать заголовки столбцов в таблице HTML от имен **RDS. DataControl** полям набора записей.  
  
 Перейти по ссылкам шаг шаг для установки и запуска сценария, а также для получения дополнительных сведений о том, как сценарий работает.  
  
 Этот сценарий содержит следующие разделы.  
  
-   [Требования к системе для приложения адресной книги](../../../ado/guide/remote-data-service/system-requirements-for-the-address-book-application.md)  
  
-   [Запуск сценария SQL адресной книги](../../../ado/guide/remote-data-service/running-the-address-book-sql-script.md)  
  
-   [Выполнение примера приложения адресной книги](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)  
  
-   [Объект привязки данных адресной книги](../../../ado/guide/remote-data-service/address-book-data-binding-object.md)  
  
-   [Кнопки команд адресной книги](../../../ado/guide/remote-data-service/address-book-command-buttons.md)  
  
-   [Кнопки навигации адресной книги](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md)  
  
## <a name="see-also"></a>См. также:  
 [Требования к системе для применение адресной книги](../../../ado/guide/remote-data-service/system-requirements-for-the-address-book-application.md)   
 [Объекты данных Microsoft ActiveX (ADO)](../../../ado/microsoft-activex-data-objects-ado.md)   
 [Принципы работы служб удаленных рабочих СТОЛОВ](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [Учебник по RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)



