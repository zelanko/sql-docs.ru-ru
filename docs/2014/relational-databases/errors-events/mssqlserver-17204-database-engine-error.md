---
title: MSSQLSERVER_17204 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 17204 (Database Engine error)
ms.assetid: 40db66f9-dd5e-478c-891e-a06d363a2552
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: e3326f262e63c658589032688c82827e86d93a9b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193795"
---
# <a name="mssqlserver17204"></a>MSSQLSERVER_17204
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17204|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBLKIO_DEVOPENFAILED|  
|Текст сообщения|%ls: Не удалось открыть файл %ls для номера файла %d.  Ошибка операционной системы: %ls.|  
  
## <a name="explanation"></a>Объяснение  
 Программе SQL Server не удалось открыть указанный файл из-за указанной ошибки.  
  
## <a name="user-action"></a>Действие пользователя  
 Определите причину, исправьте ошибку операционной системы, затем еще раз попытайтесь выполнить операцию.  
  
  