---
title: Адрес объекта привязки данных книги | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS scenarios [ADO], data-binding object
- address book application scenario [ADO], data-binding object
ms.assetid: 080c1925-d453-4b89-92ac-c93591490518
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: da63965c867c56572956ca5400a4b9dcc1281abf
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2018
ms.locfileid: "51601915"
---
# <a name="address-book-data-binding-object"></a>Объект привязки данных адресной книги
В приложении адресной книги используется [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта для привязки данных из базы данных SQL Server для визуального объекта (в данном случае таблице DHTML) на странице приложения клиента HTML. Использует управляемую событиями логику программы VBScript [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) для:  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
-   Запрос к базе данных, отправки обновлений в базу данных и обновить сетку данных.  
  
-   Позволяет пользователю переход к первой, затем предыдущей, или последнюю запись в сетке данных.  
  
 В следующем коде определяется **RDS. DataControl** компонента:  
  
```vb
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
   ID=DC1 Width=1 Height=1>  
   <PARAM NAME="SERVER" VALUE="https://<%=Request.ServerVariables("SERVER_NAME")%>">  
   <PARAM NAME="CONNECT" VALUE="Provider=sqloledb;  
Initial Catalog=AddrBookDb;Integrated Security=SSPI;">  
</OBJECT>  
```  
  
 Тег ОБЪЕКТА определяет **RDS. DataControl** компонент в программе. Тег включает два типа параметров:  
  
-   Элементами, связанными с универсального тега ОБЪЕКТА.  
  
-   Те, которые относятся к **RDS. DataControl** объекта.  
  
## <a name="generic-object-tag-parameters"></a>Универсальный объект параметров Tag  
 Ниже перечислены параметры, связанные с тегом ОБЪЕКТА.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|***ИДЕНТИФИКАТОР КЛАССА***|Уникальный 128-разрядный номер, определяющий тип внедренного объекта в системе. Этот идентификатор сохраняется в реестре локального компьютера. (Для классов идентификаторах **RDS. DataControl** объекта, см. в разделе [RDS. Объект DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md).)|  
|***Идентификатор***|Определяет идентификатор по всему документу для внедренного объекта, который используется для его идентификации в коде.|  
  
## <a name="rdsdatacontrol-tag-parameters"></a>RDS. Параметры тега DataControl  
 В следующей таблице описаны параметры, относящиеся к **RDS. DataControl** объекта. (Полный список **RDS. DataControl** объект параметров, с указанием их реализации, см. в разделе [RDS. Объект DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md).)  
  
|Параметр|Описание|  
|---------------|-----------------|  
|[СЕРВЕР](../../../ado/reference/rds-api/server-property-rds.md)|При использовании HTTP, значением является имя компьютера сервера, предшествует `https://`.|  
|[CONNECT](../../../ado/reference/rds-api/connect-property-rds.md)|Предоставляет необходимые сведения о подключении для **RDS. DataControl** для подключения к SQL Server.|  
|[SQL](../../../ado/reference/rds-api/sql-property.md)|Задает или возвращает строку запроса, используемый для получения [записей](../../../ado/reference/ado-api/recordset-object-ado.md).|  
  
## <a name="see-also"></a>См. также  
 [Кнопки команд адресной книги](../../../ado/guide/remote-data-service/address-book-command-buttons.md)


