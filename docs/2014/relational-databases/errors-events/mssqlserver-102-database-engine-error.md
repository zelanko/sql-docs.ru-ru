---
title: MSSQLSERVER_102 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 102 (Database Engine error)
ms.assetid: 264dc1a2-c8a0-4c89-b5f6-951baf950299
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fa6c196eb323497817753abda7cdccb0492cd286
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554199"
---
# <a name="mssqlserver_102"></a>MSSQLSERVER_102
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
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
  
  
