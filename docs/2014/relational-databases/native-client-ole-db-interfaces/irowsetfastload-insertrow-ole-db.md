---
title: 'IRowsetFastLoad:: InsertRow (OLE DB) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IRowsetFastLoad::InsertRow (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- InsertRow method
ms.assetid: 594d3461-34d2-41e7-8ad4-bd2753601ab6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9c4cd4aff0a8868b8870374fcffb8c7b7169fe2e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62511633"
---
# <a name="irowsetfastloadinsertrow-ole-db"></a>IRowsetFastLoad::InsertRow (OLE DB)
  Добавляет строку в набор строк для массового копирования. Примеры см. в разделе [копирование данных использование IRowsetFastLoad &#40;OLE DB&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) и [Отправка данных больших двоичных объектов в SQL Server с помощью IRowsetFastLoad и ISEQUENTIALSTREAM ](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)&#40;OLE DB.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT InsertRow(  
HACCESSOR  
hAccessor  
,  
void*  
pData  
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *HACCESSOR*[in]  
 Дескриптор метода доступа, определяющий данные строк для массового копирования. Указанный метод доступа является методом доступа к строке, связывающий память потребителя, содержащую значения данных.  
  
 *pData*[вход]  
 Указатель на память потребителя, содержащую значения данных. Дополнительные сведения см. в разделе [Структуры DBBINDING](https://go.microsoft.com/fwlink/?LinkId=65955).  
  
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
 Этот метод был вызван применительно к набору строк массового копирования, который ранее стал недействительным в результате выполнения метода [IRowsetFastLoad::Commit](irowsetfastload-commit-ole-db.md).  
  
 DB_E_BADACCESSORHANDLE  
 Потребитель предоставил недопустимый аргумент *hAccessor* .  
  
 DB_E_BADACCESSORTYPE  
 Указанный метод доступа не является методом доступа к строке или не указывает память потребителя.  
  
## <a name="remarks"></a>Remarks  
 Ошибка при преобразовании данных потребителя в тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для столбца приводит к тому, что поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает E_FAIL. Данные могут передаваться в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] любым методом **InsertRow** или только методом **Commit**. Приложение потребителя может вызывать метод **InsertRow** много раз с ошибочными данными, прежде чем получит уведомление, что при преобразовании типов данных произошла ошибка. Поскольку метод **Commit** гарантирует, что все данные были правильно указаны потребителем, потребитель может при необходимости использовать метод **Commit** для проверки данных.  
  
 Наборы строк для массового копирования поставщиком OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доступны только для записи. Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не предоставляет методов, позволяющих потребителю запрашивать наборы строк. Чтобы прервать обработку, потребитель может освободить ссылку на интерфейс [IRowsetFastLoad](irowsetfastload-ole-db.md), не вызывая метод **Commit**. Невозможно получить доступ к вставленной потребителем строке, изменить ее значения или удалить ее из набора строк.  
  
 Массово скопированные строки форматируются на сервере для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Формат строки зависит от любых параметров, которые могли быть заданы для соединения или сеанса, например ANSI_PADDING. Этот параметр по умолчанию включен для любого соединения, установленного с помощью поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [IRowsetFastLoad &#40;OLE DB&#41;](irowsetfastload-ole-db.md)  
  
  
