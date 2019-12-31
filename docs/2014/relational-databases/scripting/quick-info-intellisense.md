---
title: Краткие сведения (технология IntelliSense)
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Quick Info option [IntelliSense]
- declarations [IntelliSense]
- IntelliSense [SQL Server], Quick Info
- identifier declarations [IntelliSense]
ms.assetid: 3c8b59f4-1922-4bde-844f-5f2306514d96
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f3c1e58fb99e23682df63903553b9167c74a82e
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75243729"
---
# <a name="quick-info-intellisense"></a>Краткие сведения (технология IntelliSense)
  При установленном параметре [!INCLUDE[msCoName](../../includes/msconame-md.md)] Краткие сведения **в технологии** IntelliSense отображается полное объявление декларации любого идентификатора в коде. При наведении указателя мыши на идентификатор его объявление отобразится в желтом всплывающем окне. В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**Краткие сведения** доступны для компонента Database Engine и редактора XML-запросов.  
  
## <a name="transact-sql-quick-info"></a>Краткие сведения по Transact-SQL  
 **Краткие сведения** отображает два типа данных в редакторе [!INCLUDE[ssDE](../../includes/ssde-md.md)] запросов. Во всех режимах, кроме режима отладки, модуль **Quick Info** отображает объявление выражения. В режиме отладки модуль **Краткие сведения** отображает имя выражения и его текущее значение.  
  
 В редакторе запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]**Краткие сведения** доступны только для поддерживаемых технологией IntelliSense частей синтаксиса [!INCLUDE[tsql](../../includes/tsql-md.md)] . Например, если навести указатель мыши на идентификатор объекта, который имеет тип данных, не поддерживаемый технологией IntelliSense, то во всплывающем окне **Краткие сведения** появится сообщение о том, что этот тип данных не поддерживается.  
  
## <a name="see-also"></a>См. также  
 [Синтаксис Transact-SQL, поддерживаемый технологией IntelliSense](transact-sql-syntax-supported-by-intellisense.md)  
  
  
