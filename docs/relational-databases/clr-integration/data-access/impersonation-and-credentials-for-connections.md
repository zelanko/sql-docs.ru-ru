---
title: Олицетворение и учетные данные для подключений | Документация Майкрософт
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
ms.openlocfilehash: d83ee1d69e7083931a2f6e6befb89912abec43f0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138680"
---
# <a name="impersonation-and-credentials-for-connections"></a>Олицетворение и учетные данные для соединений
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В условиях интеграции [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] со средой CLR использовать проверку подлинности Windows сложнее, чем проверку подлинности SQL Server, но более безопасно. При использовании проверки подлинности Windows имейте ввиду следующие замечания.  
  
 По умолчанию процесс SQL Server, который подключается к Windows, приобретает контекст безопасности учетной записи службы Windows SQL Server. Однако возможно также сопоставить функцию CLR с удостоверением-посредником, чтобы у исходящих соединений был контекст безопасности, отличный от учетной записи службы Windows.  
  
 В некоторых случаях может потребоваться олицетворять вызывающий объект с помощью **SqlContext.WindowsIdentity** свойству, а не выполняется как учетная запись службы. **WindowsIdentity** экземпляр представляет удостоверение клиента, запустившего вызывающий код, который доступен, только если клиент использовал проверку подлинности Windows. После получения **WindowsIdentity** экземпляр, можно вызвать **Impersonate** изменить токен безопасности потока и затем открыть соединения ADO.NET от имени клиента.  
  
 После вызова SQLContext.WindowsIdentity.Impersonate, не может получить доступ к локальным данным и не может получить доступ к системных данных. Для доступа к данным, необходимо вызвать WindowsImpersonationContext.Undo.  
  
 В следующем примере показано, как олицетворять вызывающий объект с помощью **SqlContext.WindowsIdentity** свойство.  
  
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
  
 Более того, если был получен экземпляр идентификатора [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, то по умолчанию нельзя перенести этот экземпляр на другой компьютер; по умолчанию инфраструктура безопасности Windows не позволяет делать этого. Однако существует механизм под названием «делегирование», который позволяет распространять идентификаторы Windows на несколько доверенных компьютеров. Дополнительные сведения о делегировании в статье TechNet «[передачу протокола Kerberos и ограниченное делегирование](https://go.microsoft.com/fwlink/?LinkId=50419)«.  
  
## <a name="see-also"></a>См. также  
 [Объект SqlContext](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
  
  
