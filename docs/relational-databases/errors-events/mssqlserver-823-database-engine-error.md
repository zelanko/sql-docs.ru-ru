---
title: Ошибка ядра СУБД MSSQLSERVER | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 823 (Database Engine error)
ms.assetid: 0d9fce3c-3772-46ce-a7a3-4f4988dc6cae
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d8cef116f673266038ef4cbbca920f33fffbcb69
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51677649"
---
# <a name="mssqlserver---database-engine-error"></a>Ошибка ядра СУБД MSSQLSERVER
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|823|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|B_HARDERR|  
|Текст сообщения|Операционная система возвратила ошибку %ls в SQL Server при %S_MSG в смещении %#016I64x файла «%ls». Дополнительные сведения см. в журнале ошибок SQL Server и журнале системных событий. Это серьезная ошибка системного уровня, которая угрожает целостности базы данных, поэтому она должна быть немедленно исправлена. Выполните полную проверку базы данных на согласованность (DBCC CHECKD). Эта ошибка может быть вызвана многими причинами. Дополнительные сведения см. в электронной документации по SQL Server.|  
  
## <a name="explanation"></a>Объяснение  
Запрос Windows на чтение или запись завершился ошибкой. Код ошибки, возвращаемой Windows, и соответствующий текст содержатся в сообщении. В случае операции чтения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] повторяет попытку чтения четыре раза. Такой сбой обычно является результатом ошибки оборудования, но в некоторых случаях причиной может являться неисправность драйвера устройства. Дополнительные сведения об ошибке 823 см. в разделе [https://support.microsoft.com/kb/828339](https://support.microsoft.com/kb/828339). Дополнительные сведения об ошибках ввода-вывода см. в [главе 2 документации Майкрософт об основных операциях ввода-вывода в SQL Server](https://go.microsoft.com/fwlink/?LinkId=69370).  
  
## <a name="user-action"></a>Действие пользователя  
Просмотрите дополнительные сведения в журнале системных событий. Свяжитесь с производителем оборудования или со специалистами поддержки пользователей Майкрософт для выяснения причин сбоя и необходимых действий по его исправлению. После исправления ошибки оборудования восстановите все базы данных и запустите DBCC CHECKDB.  
  
