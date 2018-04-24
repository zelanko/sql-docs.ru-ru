---
title: Адрес объекта привязки к данным книги | Документы Microsoft
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
- RDS scenarios [ADO], data-binding object
- address book application scenario [ADO], data-binding object
ms.assetid: 080c1925-d453-4b89-92ac-c93591490518
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 353e086d8350364a07486eba2334c76b470237db
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="address-book-data-binding-object"></a>Объект привязки данных адресной книги
Адресная книга приложение использует [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта привязывать данные из базы данных SQL Server для визуального объекта (в данном случае таблице DHTML) на странице приложения клиента HTML. Использует управляемую событиями логику программы VBScript [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) для:  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
-   Запрос к базе данных, отправки обновлений в базу данных и обновления данных сетки.  
  
-   Предоставить пользователям возможность перемещения к первой, затем предыдущей, или последней записи в сетке данных.  
  
 В следующем коде определяется **RDS. DataControl** компонента:  
  
```  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
   ID=DC1 Width=1 Height=1>  
   <PARAM NAME="SERVER" VALUE="http://<%=Request.ServerVariables("SERVER_NAME")%>">  
   <PARAM NAME="CONNECT" VALUE="Provider=sqloledb;  
Initial Catalog=AddrBookDb;Integrated Security=SSPI;">  
</OBJECT>  
```  
  
 Тег ОБЪЕКТА определяет **RDS. DataControl** компонент в программе. Тег содержит два типа параметров:  
  
-   Элементами, связанными с универсальным тега OBJECT.  
  
-   Те, относящиеся к **RDS. DataControl** объекта.  
  
## <a name="generic-object-tag-parameters"></a>Параметры универсального ОБЪЕКТА тега  
 Ниже перечислены параметры, связанные с тега OBJECT.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|***CLASSID***|Уникальный 128-разрядный номер, определяющий тип внедренного объекта в системе. Этот идентификатор сохраняется в реестре локального компьютера. (Для класса идентификаторы **RDS. DataControl** см. в разделе [RDS. Объект DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md).)|  
|***Идентификатор***|Определяет идентификатор уровня документа для внедренного объекта, который используется для его идентификации в коде.|  
  
## <a name="rdsdatacontrol-tag-parameters"></a>RDS. Параметры DataControl тег  
 В следующей таблице описаны параметры, относящиеся к **RDS. DataControl** объекта. (Полный список **RDS. DataControl** объекта, параметры и способы их реализации см. в разделе [RDS. Объект DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md).)  
  
|Параметр|Описание|  
|---------------|-----------------|  
|[СЕРВЕР](../../../ado/reference/rds-api/server-property-rds.md)|При использовании HTTP присваивается имя компьютера сервера, предшествующим `http://`.|  
|[CONNECT](../../../ado/reference/rds-api/connect-property-rds.md)|Предоставляет сведения о соединении, необходимые для **RDS. DataControl** для подключения к SQL Server.|  
|[SQL](../../../ado/reference/rds-api/sql-property.md)|Задает или возвращает строку запроса, используемый для получения [записей](../../../ado/reference/ado-api/recordset-object-ado.md).|  
  
## <a name="see-also"></a>См. также  
 [Кнопки команд адресной книги](../../../ado/guide/remote-data-service/address-book-command-buttons.md)


