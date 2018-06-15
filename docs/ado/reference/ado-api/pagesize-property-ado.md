---
title: Свойства PageSize (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::PageSize
helpviewer_keywords:
- PageSize property [ADO]
ms.assetid: e57930a6-46c4-4a17-a3b6-f79e94d5c9c7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aea2e9510f80f8cd0d15bfbc2f7f544055b65884
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280063"
---
# <a name="pagesize-property-ado"></a>Свойства PageSize (ADO)
Указывает, сколько записей составляют одну страницу в [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **длинные** значение, указывающее, сколько записей на странице. Значение по умолчанию — **10**.  
  
## <a name="remarks"></a>Примечания  
 Используйте **PageSize** свойства, чтобы определить, сколько записей составляют логической страницы данных. Установка размера страницы позволяет использовать [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) свойство для перехода к первой записи определенной страницы. Это полезно в сценариях веб сервера, если вы хотите разрешить пользователю перемещение по данным, Просмотр определенного числа записей за раз.  
  
 Это свойство можно задать в любое время, и его значение будет использоваться для расчета расположение первой записи определенной страницы.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [AbsolutePage, PageCount и пример свойства PageSize (Visual Basic)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage, PageCount и пример свойства PageSize (VC ++)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [Свойство AbsolutePage (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [Свойство PageCount (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)
