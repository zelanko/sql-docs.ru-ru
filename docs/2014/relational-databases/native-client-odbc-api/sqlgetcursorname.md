---
title: SQLGetCursorName | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetCursorName function
ms.assetid: 3a427a23-28ef-49aa-b9ec-6cab0914bdf3
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6262c913a0b7f3060b0c48f9061cab90345f99ab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096156"
---
# <a name="sqlgetcursorname"></a>SQLGetCursorName
  Если приложение не указывает имени курсора, драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует его для приложения после создании курсора. Приложение может использовать **SQLGetCursorName** , чтобы получить определенное драйвером имя курсора для позиционированных инструкций UPDATE и DELETE. Приложению не требуется вызывать **SQLSetCursorName** , чтобы использовать преимущества позиционированных инструкций по обработке данных.  
  
## <a name="see-also"></a>См. также  
 [Функция SQLGetCursorName](http://go.microsoft.com/fwlink/?LinkId=59349)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  