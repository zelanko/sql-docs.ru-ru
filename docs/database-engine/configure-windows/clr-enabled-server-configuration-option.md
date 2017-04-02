---
title: "Параметр конфигурации сервера &#171;clr enabled&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "сборки [интеграция со средой CLR], проверка выполнения"
  - "clr enabled, параметр"
ms.assetid: 0722d382-8fd3-4fac-b4a8-cd2b7a7e0293
caps.latest.revision: 36
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 36
---
# Параметр конфигурации сервера &#171;clr enabled&#187;
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Используйте параметр «clr enabled», чтобы указать, может ли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнять пользовательские сборки. Параметр clr enabled принимает перечисленные ниже значения. 
  
|Значение|Описание|  
|-----------|-----------------|  
|0|Выполнение сборок не разрешается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|1|Выполнение сборок разрешается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
Только в WOW64. Перезагрузите серверы WOW64, чтобы изменения параметров вступили в силу. Для других типов серверов перезагрузка не требуется.  

При выполнении инструкции RECONFIGURE и изменении значения параметра clr enabled с 1 на 0 все домены приложений, содержащие пользовательские сборки, немедленно выгружаются.  
  
>  **Запуск среды CLR не поддерживается при использовании упрощенных пулов**. Отключите один из двух параметров: "clr enabled" или "lightweight pooling". Функции, зависящие от среды CLR и неправильно работающие в режиме волокон, включают **иерархический** тип данных, репликацию и управление на основе политик.  
  
## Пример  
 В следующем примере сначала отображается текущая настройка параметра clr enabled, а затем параметр включается с заданием значения 1. Чтобы отключить этот параметр, задайте значение 0.  
  
```tsql  
EXEC sp_configure 'clr enabled';  
EXEC sp_configure 'clr enabled' , '1';  
RECONFIGURE;    
```  
  
## См. также:  
 [Параметр конфигурации сервера «использование упрощенных пулов»](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Параметр конфигурации сервера «использование упрощенных пулов»](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)  
  
  