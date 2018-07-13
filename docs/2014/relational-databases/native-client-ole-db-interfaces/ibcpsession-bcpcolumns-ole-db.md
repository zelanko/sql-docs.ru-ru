---
title: IBCPSession::BCPColumns (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPColumns (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPColumns method
ms.assetid: c338abe8-9e30-4853-a7c6-b1a6c00095e1
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a1fc6c8da0e46ac40bf6ddd2fbd821cdd6986dc8
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426343"
---
# <a name="ibcpsessionbcpcolumns-ole-db"></a>IBCPSession::BCPColumns (OLE DB)
  Задает количество полей для привязки к столбцам в таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT BCPColumns(   
DBCOUNTITEMnColumns);  
```  
  
## <a name="remarks"></a>Примечания  
 Он вызывает [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) для задания значений по умолчанию для полей данных. Эти значения по умолчанию получаются из информации о столбце SQL Server, которая внутренним образом возвращает поставщик, когда имя таблицы указывается через [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md).  
  
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
 Произошла ошибка поставщика; Подробные сведения, используйте [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) интерфейс.  
  
 E_UNEXPECTED  
 Непредвиденный вызов метода. Например, перед вызовом этого метода не был вызван метод **BCPInit** . Это значение возвращается также, если данный метод был вызван несколько раз для операции массового копирования.  
  
 E_OUTOFMEMORY  
 Недостаточно памяти.  
  
## <a name="see-also"></a>См. также  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [Выполнение операций массового копирования](../native-client/features/performing-bulk-copy-operations.md)  
  
  
