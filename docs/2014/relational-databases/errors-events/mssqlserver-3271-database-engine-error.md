---
title: MSSQLSERVER_3271 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 3271 (Database Engine error)
ms.assetid: 21b8de4b-6624-4163-9561-1a6cc8fe3d51
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2a0f6a1583d4437a351b68739ce85bbb5f2154f2
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427943"
---
# <a name="mssqlserver3271"></a>MSSQLSERVER_3271
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3271|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DMPIO_IO_ERROR|  
|Текст сообщения|Произошла неустранимая ошибка ввода-вывода в файле "%ls:" %ls.|  
  
## <a name="explanation"></a>Объяснение  
 Это общая ошибка, возникающая, когда происходит ошибка ввода-вывода операционной системы во время операций резервного копирования или восстановления. В большинстве ситуаций причина состоит в том, что переполняется носитель данных резервных копий.  
  
 Эта ошибка может содержать дополнительное сообщение операционной системы, указывающее, что диск заполнен. При выполнении операций резервного копирования или восстановления с помощью программ сторонних разработчиков может появляться дополнительное сообщение, указывающее на ошибку резервного копирования. Это сообщение может напоминать следующий текст:  
  
```  
"2005-08-02 16:05:16.04 spid55 Error: 18210, Severity: 16, State: 1.  
 2005-08-02 16:05:16.04 spid55 BackupVirtualDeviceFile  
::RequestDurableMedia: Flush failure on backup device 'VDINULL'.   
Operating system error 995(The I/O operation has been aborted because   
of either a thread exit or an application request.)."  
```  
  
 Оно указывает на то, что программа резервного копирования запросила завершение резервного копирования или восстановления.  
  
## <a name="user-action"></a>Действие пользователя  
 При необходимости выполните следующие действия.  
  
-   Для определения причины этой неполадки просмотрите сообщения об ошибках операционной системы и SQL Server, предшествующие ей.  
  
-   Убедитесь в наличии достаточного места на носителе резервных данных.  
  
-   Исправьте все ошибки, возникшие в программе резервного копирования и восстановления данных от сторонних разработчиков.  
  
  
