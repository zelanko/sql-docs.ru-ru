---
title: Олицетворение и учетные данные для подключений Документы Майкрософт
description: В интеграции S'L Server CLR вы можете выдать себя за вызывающего абонента в windows Authentication с помощью свойства SqlContext.WindowsIdentity.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- authentication [CLR integration]
- user impersonation [CLR integration]
- credentials [CLR integration]
- database objects [CLR integration], security
ms.assetid: 293dce7d-1db2-4657-992f-8c583d6e9ebb
author: rothja
ms.author: jroth
ms.openlocfilehash: 382185c036055bb9ea689f551c256a26ee83b0b4
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81485355"
---
# <a name="impersonation-and-credentials-for-connections"></a>Олицетворение и учетные данные для соединений
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В условиях интеграции [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] со средой CLR использовать проверку подлинности Windows сложнее, чем проверку подлинности SQL Server, но более безопасно. При использовании проверки подлинности Windows имейте ввиду следующие замечания.  
  
 По умолчанию процесс SQL Server, который подключается к Windows, приобретает контекст безопасности учетной записи службы Windows SQL Server. Однако возможно также сопоставить функцию CLR с удостоверением-посредником, чтобы у исходящих соединений был контекст безопасности, отличный от учетной записи службы Windows.  
  
 В некоторых случаях вы можете выдать себя за вызывающего абонента, используя свойство **SqlContext.WindowsIdentity** вместо того, чтобы работать в качестве учетной записи службы. Экземпляр **WindowsIdentity** представляет личность клиента, который ссылался на код вызова, и доступен только тогда, когда клиент использовал аутентификацию Windows. После получения экземпляра **WindowsIdentity** можно вызвать **Impersonate,** чтобы изменить маркер безопасности потока, а затем открыть ADO.NET соединения от имени клиента.  
  
 После вызова S'LContext.WindowsIdentity.Impersone вы не можете получить доступ к локальным данным и не можете получить доступ к системным данным. Чтобы получить доступ к данным снова, вы должны вызвать WindowsImpersonationContext.Undo.  
  
 Ниже приводится следующий пример, как выдавать себя за вызывающего абонента с помощью свойства **SqlContext.WindowsIdentity.**  
  
 Visual C#  
  
```  
WindowsIdentity clientId = null;  
WindowsImpersonationContext impersonatedUser = null;  
  
clientId = SqlContext.WindowsIdentity;  
  
// This outer try block is used to protect from   
// exception filter attacks which would prevent  
// the inner finally block from executing and   
// resetting the impersonation.  
try  
{  
   try  
   {  
      impersonatedUser = clientId.Impersonate();  
      if (impersonatedUser != null)  
         return GetFileDetails(directoryPath);  
         else return null;  
   }  
   finally  
   {  
      if (impersonatedUser != null)  
         impersonatedUser.Undo();  
   }  
}  
catch  
{  
   throw;  
}  
```  
  
> [!NOTE]  
>  Для получения информации об изменениях в поведении в олицетворении [см.](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md)  
  
 Более того, если был получен экземпляр идентификатора [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, то по умолчанию нельзя перенести этот экземпляр на другой компьютер; по умолчанию инфраструктура безопасности Windows не позволяет делать этого. Однако существует механизм под названием «делегирование», который позволяет распространять идентификаторы Windows на несколько доверенных компьютеров. Подробнее о делегировании читайте в материале журнала "Огонек"["Переход Керберосского протокола и ограниченная делегация".](https://go.microsoft.com/fwlink/?LinkId=50419)  
  
## <a name="see-also"></a>См. также:  
 [Объект SqlContext](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
  
  
