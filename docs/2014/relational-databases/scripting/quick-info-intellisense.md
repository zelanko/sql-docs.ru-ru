---
title: Краткие сведения (IntelliSense) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Quick Info option [IntelliSense]
- declarations [IntelliSense]
- IntelliSense [SQL Server], Quick Info
- identifier declarations [IntelliSense]
ms.assetid: 3c8b59f4-1922-4bde-844f-5f2306514d96
caps.latest.revision: 32
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a0ebfe062b9f1d1ad837dd1cf5506c4610bb25a9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097279"
---
# <a name="quick-info-intellisense"></a>Краткие сведения (технология IntelliSense)
  При установленном параметре [!INCLUDE[msCoName](../../includes/msconame-md.md)] Краткие сведения **в технологии** IntelliSense отображается полное объявление декларации любого идентификатора в коде. При наведении указателя мыши на идентификатор его объявление отобразится в желтом всплывающем окне. В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Краткие сведения** доступны для компонента Database Engine и редактора XML-запросов.  
  
## <a name="transact-sql-quick-info"></a>Краткие сведения по Transact-SQL  
 Модуль**Краткие сведения** отображает в редакторе запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] два типа сведений. Во всех режимах, кроме режима отладки, модуль **Quick Info** отображает объявление выражения. В режиме отладки модуль **Краткие сведения** отображает имя выражения и его текущее значение.  
  
 В редакторе запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] **Краткие сведения** доступны только для поддерживаемых технологией IntelliSense частей синтаксиса [!INCLUDE[tsql](../../includes/tsql-md.md)] . Например, если навести указатель мыши на идентификатор объекта, который имеет тип данных, не поддерживаемый технологией IntelliSense, то во всплывающем окне **Краткие сведения** появится сообщение о том, что этот тип данных не поддерживается.  
  
## <a name="see-also"></a>См. также  
 [Синтаксис языка Transact-SQL, поддерживаемый технологией IntelliSense](transact-sql-syntax-supported-by-intellisense.md)  
  
  