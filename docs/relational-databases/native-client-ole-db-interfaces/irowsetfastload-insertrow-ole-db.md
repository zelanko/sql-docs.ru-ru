---
title: IRowsetFastLoad::InsertRow (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRowsetFastLoad::InsertRow (OLE DB)
apitype: COM
helpviewer_keywords:
- InsertRow method
ms.assetid: 594d3461-34d2-41e7-8ad4-bd2753601ab6
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 404068023a2a62739286134f8fda08184e4844c8
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39562518"
---
# <a name="irowsetfastloadinsertrow-ole-db"></a>IRowsetFastLoad::InsertRow (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Добавляет строку в набор строк для массового копирования. Примеры, см. в разделе [массового копирования данных с помощью IRowsetFastLoad &#40;OLE DB&#41; ](../../relational-databases/native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) и [отправить данные больших двоичных ОБЪЕКТОВ SQL SERVER с помощью IROWSETFASTLOAD и ISEQUENTIALSTREAM &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT InsertRow(  
      HACCESSOR hAccessor,  
      void* pData);  
```  
  
## <a name="arguments"></a>Аргументы  
 *hAccessor*[in]  
 Дескриптор метода доступа, определяющий данные строк для массового копирования. Указанный метод доступа является методом доступа к строке, связывающий память потребителя, содержащую значения данных.  
  
 *pData*[in]  
 Указатель на память потребителя, содержащую значения данных. Дополнительные сведения см. в разделе [Структуры DBBINDING](http://go.microsoft.com/fwlink/?LinkId=65955).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод выполнен успешно. Любые связанные значения состояния для всех столбцов имеют значение DBSTATUS_S_OK или DBSTATUS_S_NULL.  
  
 E_FAIL  
 Произошла ошибка. Сведения об ошибках можно получить с помощью интерфейса обработки ошибок набора строк.  
  
 E_INVALIDARG  
 Аргумент *pData* содержит указатель NULL.  
  
 E_OUTOFMEMORY  
 SQLNCLI11 не удалось выделить достаточно памяти для завершения запроса.  
  
 E_UNEXPECTED  
 Этот метод был вызван применительно к набору строк массового копирования, который ранее стал недействительным в результате выполнения метода [IRowsetFastLoad::Commit](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-commit-ole-db.md).  
  
 DB_E_BADACCESSORHANDLE  
 Потребитель предоставил недопустимый аргумент *hAccessor* .  
  
 DB_E_BADACCESSORTYPE  
 Указанный метод доступа не является методом доступа к строке или не указывает память потребителя.  
  
## <a name="remarks"></a>Примечания  
 Ошибка при преобразовании данных потребителя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных для столбца приводит к возвращает E_FAIL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента. Данные могут передаваться в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] любым методом **InsertRow** или только методом **Commit**. Приложение потребителя может вызывать метод **InsertRow** много раз с ошибочными данными, прежде чем получит уведомление, что при преобразовании типов данных произошла ошибка. Поскольку метод **Commit** гарантирует, что все данные были правильно указаны потребителем, потребитель может при необходимости использовать метод **Commit** для проверки данных.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Групповое копирование наборов строк OLE DB для собственного клиента поставщика доступны только для записи. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента не предоставляет методов, позволяющих потребителю запрашивать набора строк. Чтобы прервать обработку, потребитель может освободить ссылку на интерфейс [IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md), не вызывая метод **Commit**. Невозможно получить доступ к вставленной потребителем строке, изменить ее значения или удалить ее из набора строк.  
  
 Массово скопированные строки форматируются на сервере для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Формат строки зависит от любых параметров, которые могли быть заданы для соединения или сеанса, например ANSI_PADDING. Этот параметр включен по умолчанию для любого соединения, установленного через [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента.  
  
## <a name="see-also"></a>См. также  
 [IRowsetFastLoad &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)  
  
  
