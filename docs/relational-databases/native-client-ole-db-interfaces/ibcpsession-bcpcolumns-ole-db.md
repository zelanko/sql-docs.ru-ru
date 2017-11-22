---
title: "IBCPSession::BCPColumns (OLE DB) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-interfaces
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IBCPSession::BCPColumns (OLE DB)
apitype: COM
helpviewer_keywords: BCPColumns method
ms.assetid: c338abe8-9e30-4853-a7c6-b1a6c00095e1
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 03a90825189295601be31dec467997bd8cfa6780
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="ibcpsessionbcpcolumns-ole-db"></a>IBCPSession::BCPColumns (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Задает количество полей для привязки к столбцам в таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT BCPColumns(   
      DBCOUNTITEM nColumns);  
```  
  
## <a name="remarks"></a>Замечания  
 Этот метод [IBCPSession::BCPColFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md) для задания значений по умолчанию для полей данных. Эти значения по умолчанию получаются из информации о столбце SQL Server, которую внутренним образом возвращает поставщик, когда имя таблицы указывается через [IBCPSession::BCPInit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md).  
  
> [!NOTE]  
>  Данный метод можно вызывать только после того, как вызван метод **BCPInit** с допустимым именем файла.  
  
 Этот метод следует вызывать только в случае, когда планируется использовать нестандартный формат пользовательского файла. Дополнительную информацию об описании стандартного формата пользовательского файла см. в справке по методу **BCPInit** .  
  
 После вызова метода **BCPColumns** следует вызвать метод **BCPColFmt** для каждого столбца в пользовательском файле, чтобы полностью описать нестандартный формат файла.  
  
## <a name="arguments"></a>Аргументы  
 *nColumns*[in]  
 Общее число полей в пользовательском файле. Даже если предполагается массовое копирование данных из пользовательского файла в таблицу SQL Server и не предполагается копирование всех полей в пользовательском файле, аргументу *nColumns* следует присвоить значение, равное общему числу полей в пользовательском файле. Затем с помощью свойства **BCPColFmt**можно указать поля, которые нужно пропустить.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод выполнен успешно.  
  
 E_FAIL  
 Ошибка поставщика; Дополнительные сведения, используйте [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) интерфейса.  
  
 E_UNEXPECTED  
 Непредвиденный вызов метода. Например, перед вызовом этого метода не был вызван метод **BCPInit** . Это значение возвращается также, если данный метод был вызван несколько раз для операции массового копирования.  
  
 E_OUTOFMEMORY  
 Недостаточно памяти.  
  
## <a name="see-also"></a>См. также:  
 [IBCPSession &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Выполнение операций массового копирования](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
