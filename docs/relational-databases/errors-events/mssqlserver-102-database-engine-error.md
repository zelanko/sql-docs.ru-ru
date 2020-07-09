---
title: MSSQLSERVER_102 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 102 (Database Engine error)
ms.assetid: 264dc1a2-c8a0-4c89-b5f6-951baf950299
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e3d51e947940fe76ce171e4f50e5add327230ff2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781539"
---
# <a name="mssqlserver_102"></a>MSSQLSERVER_102
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
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
  
