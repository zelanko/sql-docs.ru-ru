---
title: IRowsetFastLoad::Commit (OLE DB) | Документация Майкрософт
description: IRowsetFastLoad::Commit (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- IRowsetFastLoad::Commit (OLE DB)
apitype: COM
helpviewer_keywords:
- Commit method
author: pmasl
ms.author: pelopes
ms.openlocfilehash: d76ad5dc881ab4f31808d738d9beacd85929d279
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67994408"
---
# <a name="irowsetfastloadcommit-ole-db"></a>IRowsetFastLoad::Commit (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Обозначает конец пакета вставляемых строк и записывает эти строки в таблицу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Примеры можно найти в статьях [Выполнение массового копирования данных с использованием интерфейса IRowsetFastLoad (OLE DB)](../../oledb/ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) и [Отправка данных BLOB-объектов в SQL Server с помощью интерфейсов IROWSETFASTLOAD и ISEQUENTIALSTREAM (OLE DB)](../../oledb/ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT Commit(  
      BOOL fDone);  
```  
  
## <a name="arguments"></a>Аргументы  
 *fDone*[in]  
 Если значение равно FALSE, то набор строк сохраняет достоверность и может использоваться пользователем для дополнительной вставки строк. Если значение равно TRUE, то набор строк теряет достоверность и пользователь не может выполнять дальнейшую вставку.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод завершился успешно, и все добавленные записи были записаны в таблицу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 E_FAIL  
 Произошла ошибка, зависящая от поставщика. Получите сведения об ошибке для конкретного текста ошибки из поставщика.  
  
 E_UNEXPECTED  
 Этот метод был вызван применительно к набору строк массового копирования, который ранее стал недействительным в результате выполнения метода **IRowsetFastLoad::Commit**.  
  
## <a name="remarks"></a>Remarks  
 Набор строк массового копирования OLE DB Driver for SQL Server ведет себя так же, как набор строк в режиме отложенного обновления. По мере вставки пользователем данных строк с помощью набора строк добавленные строки обрабатываются таким же образом, как и ожидающие выполнения вставки для набора строк, поддерживающего **IRowsetUpdate**.  
  
 Пользователь должен вызвать метод **Commit** применительно к набору строк массового копирования, чтобы записать добавленные строки в таблицу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таким же образом, как и при использовании метода **IRowsetUpdate::Update** для отправки ожидающих строк в экземпляр SQL Server.  
  
 Если пользователь освобождает ссылку на набор данных массового копирования, не вызывая метод **Commit**, то все добавленные строки, которые не были записаны, теряются.  
  
 Пользователь может сгруппировать добавленные строки, вызывая метод **Commit** с аргументом *fDone* в значении FALSE. Если аргумент *fDone* установлен в значение TRUE, то набор строк становится недействительным. Недействительным набором строк массового копирования поддерживаются только интерфейс **ISupportErrorInfo** и метод **IRowsetFastLoad::Release**.  
  
## <a name="see-also"></a>См. также:  
 [IRowsetFastLoad (OLE DB)](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)  
  
  
