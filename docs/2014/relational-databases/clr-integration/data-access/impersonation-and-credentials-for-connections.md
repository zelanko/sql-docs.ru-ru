---
title: Олицетворение и учетные данные для подключения | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f2cc3fc4695c9e0b2a723668f09fc1bf388dabaa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192898"
---
# <a name="impersonation-and-credentials-for-connections"></a>Олицетворение и учетные данные для соединений
  В условиях интеграции [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] со средой CLR использовать проверку подлинности Windows сложнее, чем проверку подлинности SQL Server, но более безопасно. При использовании проверки подлинности Windows имейте ввиду следующие замечания.  
  
 По умолчанию процесс SQL Server, который подключается к Windows, приобретает контекст безопасности учетной записи службы Windows SQL Server. Однако возможно также сопоставить функцию CLR с удостоверением-посредником, чтобы у исходящих соединений был контекст безопасности, отличный от учетной записи службы Windows.  
  
 В некоторых случаях бывает необходимо олицетворить вызывающего при помощи свойства `SqlContext.WindowsIdentity`, а не запускать его, как учетную запись службы. Экземпляр `WindowsIdentity` представляет идентификатор клиента, запустившего вызывающий код, и его можно использовать только если клиент использовал проверку подлинности Windows. Получив экземпляр `WindowsIdentity`, можно вызвать метод `Impersonate`, чтобы изменить токен безопасности потока, а затем открыть соединения ADO.NET от имени клиента.  
  
 После вызова SQLContext.WindowsIdentity.Impersonate, получить доступ к локальным данным и не доступ к системным данным. Для доступа к данным, необходимо вызвать WindowsImpersonationContext.Undo.  
  
 В следующем примере показано, как выполнять олицетворение вызывающего объекта с помощью свойства `SqlContext.WindowsIdentity`.  
  
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
>  Сведения об изменениях поведения при олицетворении см. в разделе [критические изменения в функциях ядра СУБД в SQL Server 2014](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md).  
  
 Более того, если был получен экземпляр идентификатора [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, то по умолчанию нельзя перенести этот экземпляр на другой компьютер; по умолчанию инфраструктура безопасности Windows не позволяет делать этого. Однако существует механизм под названием «делегирование», который позволяет распространять идентификаторы Windows на несколько доверенных компьютеров. Дополнительные сведения о делегировании в статье TechNet «[переход протокола Kerberos и ограниченное делегирование](http://go.microsoft.com/fwlink/?LinkId=50419)».  
  
## <a name="see-also"></a>См. также  
 [Объект SqlContext](../../clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
  
  