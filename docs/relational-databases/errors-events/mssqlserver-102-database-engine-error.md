---
title: "MSSQLSERVER_102 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 102 (Database Engine error)
ms.assetid: 264dc1a2-c8a0-4c89-b5f6-951baf950299
caps.latest.revision: 8
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d4184a493ecfcb3d22c8e6e6fdd93b8e9fe756a9
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver102"></a>MSSQLSERVER_102
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|102|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|P_SYNTAXERR2|  
|Текст сообщения|Неправильный синтаксис около "%.*ls".|  
  
## <a name="explanation"></a>Объяснение  
Указывает на синтаксическую ошибку. Дополнительная информация недоступна из-за того, что ошибка мешает компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)] обработать инструкцию.  
  
Может быть вызвана попыткой создать симметричный ключ с помощью устаревшего шифрования RC4 или RC4_128 при нахождении не в режимах совместимости 90 или 100.  
  
## <a name="user-action"></a>Действие пользователя  
Проверьте инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] на наличие синтаксических ошибок.  
  
При создании симметричного ключа с помощью RC4 или RC4_128 выберите более новое шифрование, например один из алгоритмов AES. (Рекомендуется.) Если необходимо использовать RC4, используйте ALTER DATABASE SET COMPATIBILITY_LEVEL, чтобы установить базу данных на уровень совместимости 90 или 100. (Не рекомендуется.)  
  

