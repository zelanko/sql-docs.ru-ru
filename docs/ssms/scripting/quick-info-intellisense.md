---
title: Краткие сведения (IntelliSense) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Quick Info option [IntelliSense]
- declarations [IntelliSense]
- IntelliSense [SQL Server], Quick Info
- identifier declarations [IntelliSense]
ms.assetid: 3c8b59f4-1922-4bde-844f-5f2306514d96
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1ce292a91733de2d1e5010d1ba1c1585ff72685a
ms.sourcegitcommit: c29150492383f48ef484fa02a483cde1cbc68aca
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65821997"
---
# <a name="quick-info-intellisense"></a>Краткие сведения (технология IntelliSense)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  При установленном параметре [!INCLUDE[msCoName](../../includes/msconame-md.md)] Краткие сведения **в технологии** IntelliSense отображается полное объявление декларации любого идентификатора в коде. При наведении указателя мыши на идентификатор его объявление отобразится в желтом всплывающем окне. В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Краткие сведения** доступны для компонента Database Engine и редактора XML-запросов.  
  
## <a name="transact-sql-quick-info"></a>Краткие сведения по Transact-SQL  
 Модуль**Краткие сведения** отображает в редакторе запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] два типа сведений. Во всех режимах, кроме режима отладки, модуль **Quick Info** отображает объявление выражения. В режиме отладки модуль **Краткие сведения** отображает имя выражения и его текущее значение.  
  
 В редакторе запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] **Краткие сведения** доступны только для поддерживаемых технологией IntelliSense частей синтаксиса [!INCLUDE[tsql](../../includes/tsql-md.md)] . Например, если навести указатель мыши на идентификатор объекта, который имеет тип данных, не поддерживаемый технологией IntelliSense, то во всплывающем окне **Краткие сведения** появится сообщение о том, что этот тип данных не поддерживается.  
  
## <a name="see-also"></a>См. также:  
 [Синтаксис языка Transact-SQL, поддерживаемый технологией IntelliSense](../../relational-databases/scripting/transact-sql-syntax-supported-by-intellisense.md)  
  
  
