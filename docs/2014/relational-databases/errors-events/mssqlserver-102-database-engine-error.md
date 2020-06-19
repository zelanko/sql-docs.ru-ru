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
ms.openlocfilehash: ac4f4d6c19eb58e9e1eb9b2eb71312f001aa5f6b
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84969864"
---
# <a name="mssqlserver_102"></a>MSSQLSERVER_102
    
## <a name="details"></a>Сведения  
  
|||  
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
  
  
