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
ms.openlocfilehash: 1db01010fea79d2badaf81588296391d7e2149f2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931767"
---
# <a name="pagesize-property-ado"></a>Свойство PageSize (ADO)
Указывает, сколько записей составляют одну страницу в [наборе записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение **типа Long** , указывающее, сколько записей находится на странице. Значение по умолчанию — **10**.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **pageSize** , чтобы определить, сколько записей составляют логическую страницу данных. Установка размера страницы позволяет использовать свойство [примеры absolutepage](../../../ado/reference/ado-api/absolutepage-property-ado.md) для перехода к первой записи определенной страницы. Это полезно в сценариях веб-сервера, когда необходимо разрешить пользователю пролистывать данные, одновременно просматривая определенное количество записей.  
  
 Это свойство может быть задано в любое время, и его значение будет использоваться для вычисления расположения первой записи определенной страницы.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры свойств примеры absolutepage, PageCount и PageSize (Visual Basic)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [Пример свойств примеры absolutepage, PageCount и PageSize (Visual c++)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [Свойство примеры absolutepage (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [Свойство PageCount (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)
