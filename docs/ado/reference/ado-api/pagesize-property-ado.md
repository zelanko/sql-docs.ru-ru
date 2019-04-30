---
title: Свойство PageSize (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::PageSize
helpviewer_keywords:
- PageSize property [ADO]
ms.assetid: e57930a6-46c4-4a17-a3b6-f79e94d5c9c7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c33b8a757e699a78c699cc87e7fd7dba26006b5d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63240086"
---
# <a name="pagesize-property-ado"></a>Свойство PageSize (ADO)
Указывает, сколько записей составляют одну страницу в [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **Long** значение, указывающее, сколько записей на странице. По умолчанию используется **10**.  
  
## <a name="remarks"></a>Примечания  
 Используйте **PageSize** свойства, чтобы определить, сколько записей составляющих логической страницы данных. Создание размер страницы, позволяет использовать [примеры AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) свойство, чтобы перейти к первой записи, определенной страницы. Это полезно в сценариях веб сервера, если вы хотите разрешить пользователю просматривать данные, Просмотр определенного числа записей за раз.  
  
 Это свойство можно задать в любое время, и его значение будет использоваться для расчета расположение первой записи определенной страницы.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры AbsolutePage, PageCount и PageSize свойства пример (Visual Basic)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [Примеры AbsolutePage, PageCount и PageSize пример свойства (Visual C++)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [Свойство AbsolutePage (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [Свойство PageCount (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)
