---
title: Репликация данных в зашифрованных столбцах (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- encryption [SQL Server], replicating data
- encryption [SQL Server replication]
- publishing [SQL Server replication], encrypted columns
ms.assetid: d1f8f586-e5a3-4a71-9391-11198d42bfa3
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 077237475b3d13044c5c24c5647e2a5285f82bb0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="replicate-data-in-encrypted-columns-sql-server-management-studio"></a>Репликация данных в зашифрованные столбцы (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Репликация позволяет публиковать данные зашифрованных столбцов. Для расшифровки и использования этих данных на подписчике ключ, который был использован при шифровании данных на издателе, должен также располагаться и на подписчике. Репликация не предоставляет безопасного механизма для передачи ключей шифрования. Необходимо вручную повторно создать ключ шифрования на подписчике. В данном разделе показано, как зашифровать столбец на издателе и убедиться в том, что ключ шифрования доступен на подписчике.  
  
 Основными шагами являются следующие:  
  
1.  Создание симметричного ключа на издателе.  
  
2.  Шифрование данных столбца с помощью симметричного ключа.  
  
3.  Публикация таблицы с зашифрованным столбцом.  
  
4.  Подписка на эту публикацию.  
  
5.  Инициализация подписки.  
  
6.  Повторное создание симметричного ключа на подписчике с использованием тех же самых значений для ALGORITHM, KEY_SOURCE и IDENTITY_VALUE, что и в первом шаге.  
  
7.  Получение доступа к данным зашифрованного столбца.  
  
> [!NOTE]  
>  Для шифрования данных столбца следует использовать симметричный ключ. Симметричный ключ сам по себе может быть защищен на издателе и подписчике различными способами.  
  
### <a name="to-create-and-replicate-encrypted-column-data"></a>Создание и репликация данных зашифрованного столбца  
  
1.  На издателе выполните инструкцию [CREATE SYMMETRIC KEY](../../../t-sql/statements/create-symmetric-key-transact-sql.md).  
  
    > [!IMPORTANT]  
    >  Значение KEY_SOURCE является важным значением, которое может быть использовано для повторного создания симметричного ключа и расшифровки данных. Значение KEY_SOURCE должно всегда храниться и передаваться с соблюдением всех мер предосторожности.  
  
2.  Чтобы открыть новый ключ, выполните инструкцию [OPEN SYMMETRIC KEY](../../../t-sql/statements/open-symmetric-key-transact-sql.md) .  
  
3.  Для шифрования данных столбца на издателе используйте функцию [EncryptByKey](../../../t-sql/functions/encryptbykey-transact-sql.md) .  
  
4.  Чтобы закрыть ключ, выполните инструкцию [CLOSE SYMMETRIC KEY](../../../t-sql/statements/close-symmetric-key-transact-sql.md) .  
  
5.  Опубликуйте таблицу, которая содержит зашифрованный столбец. Дополнительные сведения см. в статье [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
6.  Подписка на эту публикацию. Дополнительные сведения см. в статьях [Создание подписки по запросу](../../../relational-databases/replication/create-a-pull-subscription.md) и [Создание принудительной подписки](../../../relational-databases/replication/create-a-push-subscription.md).  
  
7.  Инициализация подписки. Дополнительные сведения см. в статье [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
8.  На подписчике выполните инструкцию [CREATE SYMMETRIC KEY](../../../t-sql/statements/create-symmetric-key-transact-sql.md) , используя те же самые значения для ALGORITHM, KEY_SOURCE и IDENTITY_VALUE, что и в первом шаге. При этом можно задать иное значение в предложении ENCRYPTION BY.  
  
    > [!IMPORTANT]  
    >  Значение KEY_SOURCE является важным значением, которое может быть использовано для повторного создания симметричного ключа и расшифровки данных. Значение KEY_SOURCE должно всегда храниться и передаваться с соблюдением всех мер предосторожности.  
  
9. Чтобы открыть новый ключ, выполните инструкцию [OPEN SYMMETRIC KEY](../../../t-sql/statements/open-symmetric-key-transact-sql.md) .  
  
10. Для расшифровки реплицируемых данных на подписчике используйте функцию [DecryptByKey](../../../t-sql/functions/decryptbykey-transact-sql.md) .  
  
11. Чтобы закрыть ключ, выполните инструкцию [CLOSE SYMMETRIC KEY](../../../t-sql/statements/close-symmetric-key-transact-sql.md) .  
  
## <a name="example"></a>Пример  
 В этом примере создается симметричный ключ, сертификат, который используется для обеспечения безопасности симметричного ключа, и главный ключ. Эти ключи создаются в базе данных публикации. В последующем они используются для создания зашифрованного столбца EncryptedCreditCardApprovalCode в таблице `SalesOrderHeader` . Этот столбец опубликован в публикации AdvWorksSalesOrdersMerge вместо незашифрованного столбца CreditCardApprovalCode. По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
 [!code-sql[HowTo#sp_PublishEncryptedColumn](../../../relational-databases/replication/codesnippet/tsql/replicate-data-in-encryp_1.sql)]  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/replicate-data-in-encryp_2.sql)]  
  
## <a name="example"></a>Пример  
 В этом примере повторно создается тот же самый симметричный ключ в базе данных подписки с помощью тех же самых значений для ALGORITHM, KEY_SOURCE и IDENTITY_VALUE, что и в первом шаге. В этом примере предполагается, что уже имеется инициализированная подписка на публикацию AdvWorksSalesOrdersMerge для репликации зашифрованного столбца. По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо хранить учетные данные в файле скрипта, следует защитить этот файл во время хранения и передачи, чтобы предотвратить несанкционированный доступ к нему.  
  
 [!code-sql[HowTo#sp_SubscriberEncryptedColumn](../../../relational-databases/replication/codesnippet/tsql/replicate-data-in-encryp_3.sql)]  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о безопасности (репликация)](../../../relational-databases/replication/security/security-overview-replication.md)   
 [Создание идентичных симметричных ключей на двух серверах](../../../relational-databases/security/encryption/create-identical-symmetric-keys-on-two-servers.md)  
  
  
