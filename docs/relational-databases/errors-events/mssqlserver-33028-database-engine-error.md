---
title: "MSSQLSERVER_33028 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 33028 (Database Engine error)
ms.assetid: c5cec0e4-0bcd-4907-826f-e7d835cfcb37
caps.latest.revision: "10"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 35fb1076d51f4b44016cb1ff4b47e9364bd0b7c0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver33028"></a>MSSQLSERVER_33028
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|33028|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SEC_CRYPTOPROV_CANTOPENSESSION|  
|Текст сообщения|Не удается открыть сеанс для %S_MSG '%.*ls'. Код ошибки поставщика: %d.|  
  
## <a name="explanation"></a>Объяснение  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не смог открыть поставщик служб шифрования, указанный в сообщении об ошибке. Поставщик служб шифрования предоставляет указанный код ошибки. Возможно, придется обратиться к поставщику служб шифрования за дополнительными сведениями об ошибке.  
  
|Код ошибки|Description|  
|--------------|---------------|  
|0|Успешно. Нет ошибки.|  
|1|Ошибка. Произошла неуказанная или непредвиденная ошибка. Дополнительные сведения об ошибке недоступны.|  
|2|Недостаточно места в буфере. Нельзя выделить пространство для поставщика служб шифрования.|  
|3|Не поддерживается. Этот поставщик служб шифрования не поддерживается данным выпуском. Выберите другой поставщик служб шифрования.|  
|4|Не найден. Указанный поставщик служб шифрования отсутствует, или пользователь не авторизован для доступа к файлам.|  
|5|Ошибка авторизации. Причиной может быть неверный пароль или имя пользователя при создании учетных данных. Может произойти, если учетные данные не существуют.|  
|6|Недопустимый аргумент. Поставщику служб шифрования передан неправильный аргумент.|  
  
## <a name="user-action"></a>Действие пользователя  
Устраните ошибку или обратитесь к поставщику служб шифрования за дополнительными сведениями.  
  
