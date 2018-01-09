---
title: "Олицетворение и учетные данные для подключения | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b3c4495b75f9464eb0e8211eeea6529264053c61
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="impersonation-and-credentials-for-connections"></a>Олицетворение и учетные данные для соединений
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] интеграция (со средой CLR) среды CLR, с использованием проверки подлинности Windows является сложным, но надежнее, чем при использовании проверки подлинности SQL Server. При использовании проверки подлинности Windows имейте ввиду следующие замечания.  
  
 По умолчанию процесс SQL Server, который подключается к Windows, приобретает контекст безопасности учетной записи службы Windows SQL Server. Однако возможно также сопоставить функцию CLR с удостоверением-посредником, чтобы у исходящих соединений был контекст безопасности, отличный от учетной записи службы Windows.  
  
 В некоторых случаях может потребоваться олицетворять вызывающий объект, с помощью **SqlContext.WindowsIdentity** свойство вместо запуск в качестве учетной записи службы. **WindowsIdentity** экземпляр представляет удостоверение клиента, запустившего вызывающий код, который доступен, только если клиент использовал проверку подлинности Windows. После получения **WindowsIdentity** экземпляр, можно вызвать **Impersonate** изменить токен безопасности потока и затем открыть соединения ADO.NET от имени клиента.  
  
 После вызова SQLContext.WindowsIdentity.Impersonate, получить доступ к локальным данным и не доступ к системным данным. Для доступа к данным, необходимо вызвать WindowsImpersonationContext.Undo.  
  
 В следующем примере показано, как олицетворять вызывающий объект, с помощью **SqlContext.WindowsIdentity** свойство.  
  
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
>  Сведения об изменениях поведения при олицетворении см. в разделе [критические изменения в функциях ядра СУБД в SQL Server 2016](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md).  
  
 Более того, если был получен экземпляр идентификатора [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, то по умолчанию нельзя перенести этот экземпляр на другой компьютер; по умолчанию инфраструктура безопасности Windows не позволяет делать этого. Однако существует механизм под названием «делегирование», который позволяет распространять идентификаторы Windows на несколько доверенных компьютеров. Дополнительные сведения о делегировании в статье TechNet «[переход протокола Kerberos и ограниченное делегирование](http://go.microsoft.com/fwlink/?LinkId=50419)».  
  
## <a name="see-also"></a>См. также:  
 [Объект SqlContext](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
  
  
