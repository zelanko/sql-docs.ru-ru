---
title: Сценарий RDS | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: a7dcad87-aaf0-4b02-9660-472f8469761c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aaeedb6dffb992ac940eebd450c63d33badb299d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47845282"
---
# <a name="rds-scenario"></a>Сценарий RDS
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Ситуация приложения адресной книге показано, как использовать службы удаленных данных (RDS) для создания простой и работы с данными веб-приложения — online корпоративной адресной книги. Этот сценарий полезен для Microsoft Visual Basic Scripting Edition (VBScript), программисты COM, которые хотят научиться использовать работы с данными элементов управления ActiveX с помощью служб удаленных рабочих СТОЛОВ и для программного обеспечения более опытным разработчикам, желающим создание ориентированных на данные веб-приложений.  
  
 Этот сценарий предполагает, что вы знаете, как использовать базовый макет теги HTML, методы привязки данных используйте DHTML и программы с элементами управления ActiveX.  
  
 После установки пакета SDK, полный исходный код для примера приложения адресной книги можно найти в каталоге SDK в samples\dataaccess\rds\AddressBook\AddressBook.asp. Чтобы просмотреть сценарий адресной книги, в Internet Explorer 4.0 или более поздней версии, введите **http://*веб-сервер*/RDS/AddressBook/AddressBook.asp** где *веб-сервер* служит именем на свой компьютер Windows NT 4.0 или Windows 2000 веб-сервера, на котором выполняется Internet Information Services (IIS) и ASP.  
  
## <a name="introduction-to-address-book"></a>Введение в адресную книгу  
 Пример приложения адресной книги предоставляет простой online адресной книги, которую можно использовать для публикации каталога с возможностью поиска как в интрасети. В адресной книге разработан таким образом, пользователь может ввести строку поиска в одно или несколько полей для запроса информации о сотрудниках. Чтобы показать основные возможности удаленной службы данных, пример приложения намеренно хранится на небольшой минимальное число объектов и полей поиска.  
  
 Интерфейс приложения состоит из следующих частей:  
  
-   Без визуального **RDS. DataControl** объект привязки данных, который используется клиентом для подключения к базе данных.  
  
-   Критерии поиска HTML текстовые поля, которые действуют как поля ввода для атрибута сотрудника.  
  
-   Кнопки HTML для создания запросов, снимите полей, обновить базу данных со сведениями о сотрудниках, Отменить отложенные изменения и перейдите по строкам данных, отображаемое в сетке.  
  
-   DHTML привязки данных для отображения данных возвращаемый запросами к серверной базы данных (через **RDS. DataControl** объект привязки данных) в таблице.  
  
-   Подпрограммы VBScript, подключения каждого из элементов, которые упоминались ранее и позволяющих им взаимодействовать. Код VBScript также используется для инициализации **RDS. DataControl** объекта и динамически создавать заголовки столбцов в таблице HTML от имен **RDS. DataControl** полям набора записей.  
  
 Перейдите по ссылкам из шага к шагу для настройки и запуска сценария и Дополнительные сведения о том, как работает сценарий.  
  
 Этот сценарий содержит следующие разделы.  
  
-   [Требования к системе для приложения адресной книги](../../../ado/guide/remote-data-service/system-requirements-for-the-address-book-application.md)  
  
-   [Запуск сценария SQL адресной книги](../../../ado/guide/remote-data-service/running-the-address-book-sql-script.md)  
  
-   [Выполнение примера приложения адресной книги](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)  
  
-   [Объект привязки данных адресной книги](../../../ado/guide/remote-data-service/address-book-data-binding-object.md)  
  
-   [Кнопки команд адресной книги](../../../ado/guide/remote-data-service/address-book-command-buttons.md)  
  
-   [Кнопки навигации адресной книги](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md)  
  
## <a name="see-also"></a>См. также  
 [Требования к системе для приложения адресной книги](../../../ado/guide/remote-data-service/system-requirements-for-the-address-book-application.md)   
 [Объекты данных Microsoft ActiveX (ADO)](../../../ado/microsoft-activex-data-objects-ado.md)   
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [Учебник по RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)


