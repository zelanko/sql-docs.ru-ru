---
title: "Ключи шифрования базы данных и SQL Server (ядро СУБД) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: security
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: keys [SQL Server], database encryption
ms.assetid: 15c0a5e8-9177-484c-ae75-8c552dc0dac0
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a1f811501db4568f9e893fdbdf64205381298368
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-and-database-encryption-keys-database-engine"></a>Ключи шифрования базы данных и SQL Server (компонент Database Engine)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует ключи шифрования для защиты данных, информации об учетных данных и соединениях, которые хранятся в серверной базе данных. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] существует два вида ключей: *симметричный* и *aсимметричный*. В симметричных ключах для шифрования и расшифровки данных используется одинаковый пароль. При использовании асимметричных ключей один пароль применяется для шифрования данных ( *открытый* ключ), а другой для расшифровки данных ( *закрытый* ключ).  
  
 Используемые в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ключи шифрования представляют собой сочетание открытых, закрытых и симметричных ключей, которые используются для защиты конфиденциальных данных. Симметричный ключ создается во время инициализации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , при первом запуске экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Этот ключ используется [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для шифрования конфиденциальных данных, которые хранятся в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Открытые и закрытые ключи создаются операционной системой и используются для защиты симметричного ключа. Пара из открытого и закрытого ключей создается для каждого экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , который сохраняет конфиденциальные данные в базе данных.  
  
## <a name="applications-for-sql-server-and-database-keys"></a>Применения ключей шифрования SQL Server и базы данных  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает два основных варианта применения ключей: *главный ключ службы* (SMK) создается на экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и для этого экземпляра, а *главный ключ базы данных* (DMK) используется для базы данных.  
  
 Главный ключ службы автоматически создается при первом запуске экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и используется для шифрования пароля связанного сервера, учетных данных или главного ключа базы данных. Главный ключ службы шифруется с помощью ключа локального компьютера и API-интерфейса защиты данных Windows. Этот API-интерфейс использует ключ, получаемый из учетных данных Windows, которые соответствуют учетной записи службы для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и учетным данным компьютера. Главный ключ службы может быть расшифрован лишь той учетной записью службы, под которой он был создан, или участником, имеющим доступ к учетным данным компьютера.  
  
 Главный ключ базы данных — это симметричный ключ, который применяется для защиты закрытых ключей сертификатов и асимметричный ключей, которые есть в базе данных. Он также может использоваться для шифрования данных, но из-за ограниченной длины не может применяться на практике для шифрования данных так же широко, как симметричный ключ.  
  
 При создании этот ключ зашифровывается с помощью алгоритма «Triple DES» и пользовательского пароля. Чтобы разрешить автоматическое шифрование главного ключа, копия этого ключа зашифровывается с помощью главного ключа службы. Ключ хранится как в базе данных, где используется ключ, так и в системной базе данных **master** .  
  
 Копия, которая хранится в базе данных **master** , автоматически обновляется при каждом изменении главного ключа. Но это поведение по умолчанию может быть изменено с помощью параметра **DROP ENCRYPTION BY SERVICE MASTER KEY** инструкции **ALTER MASTER KEY** . Главный ключ базы данных, который не зашифрован с помощью главного ключа службы, следует открывать с помощью инструкции **OPEN MASTER KEY** и пароля.  
  
## <a name="managing-sql-server-and-database-keys"></a>Управление ключами SQL Server и базы данных  
 Управление ключами шифрования заключается в создании новых ключей базы данных, создании резервной копии ключей сервера и базы данных и знании порядка восстановления, удаления и смены ключей.  
  
 Чтобы управлять симметричными ключами, можно использовать средства, входящие в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , для выполнения следующих действий:  
  
-   Резервное копирование копии ключа сервера и базы данных, чтобы использовать их при восстановлении установки сервера или в ходе запланированного переноса.  
  
-   Восстановление ранее сохраненного ключа в базе данных. Это позволяет новому экземпляру сервера обращаться к существующим данным, которые первоначально шифровались не им.  
  
-   Удаление зашифрованных данных из базы данных в маловероятной ситуации, когда не удается обратиться к зашифрованным данным.  
  
-   Повторное создание ключей и повторное шифрование данных в маловероятной ситуации, когда ключ становится известен посторонним. Для повышения безопасности следует периодически повторно создавать ключи (например, раз в несколько месяцев) для защиты сервера от атак с целью расшифровки ключа.  
  
-   Добавление или удаление экземпляра сервера из масштабного развертывания, когда несколько серверов используют одну базу данных и ключ, допускающий обратимое шифрование для этой базы данных.  
  
## <a name="important-security-information"></a>Важная информация по безопасности  
 Для доступа к объектам, защищенным главным ключом службы, необходима учетная запись службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , которая использовалась для создания ключа, или учетная запись компьютера. То есть, компьютер привязан к системе, в которой был создан ключ. Можно изменить учетную запись службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] *или* учетную запись компьютера, не теряя доступа к ключу. Однако если изменить обе учетные записи, доступ к главному ключу службы будет потерян. Если доступ к главному ключу службы будет потерян без одного из этих элементов, то не удастся расшифровать данные и объекты, зашифрованные с помощью первоначального ключа.  
  
 Соединения, защищенные с помощью главного ключа службы, не могут быть восстановлены без него.  
  
 Для доступа к объектам и данным, защищенным главным ключом базы данных, требуется только пароль, использованный для защиты ключа.  
  
> [!CAUTION]  
>  Если любой доступ к описанным выше ключам потерян, будет потерян доступ к объектам, соединениям и данным, защищенным этими ключами. Можно восстановить главный ключ службы, как описано в приведенных ссылках, или вернуться к первоначальной системе шифрования, чтобы восстановить доступ. Не существует аварийного способа восстановления доступа.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Service Master Key](../../../relational-databases/security/encryption/service-master-key.md)  
 Дано краткое объяснение главного ключа службы и рекомендации.  
  
 [Расширенное управление ключами &#40;EKM&#41;](../../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
 Объясняется, как использовать сторонние системы управления ключами с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Создание резервной копии главного ключа службы](../../../relational-databases/security/encryption/back-up-the-service-master-key.md)  
  
 [Восстановление главного ключа службы](../../../relational-databases/security/encryption/restore-the-service-master-key.md)  
  
 [Создание главного ключа базы данных](../../../relational-databases/security/encryption/create-a-database-master-key.md)  
  
 [Создание резервной копии главного ключа базы данных](../../../relational-databases/security/encryption/back-up-a-database-master-key.md)  
  
 [Восстановление главного ключа базы данных](../../../relational-databases/security/encryption/restore-a-database-master-key.md)  
  
 [Создание идентичных симметричных ключей на двух серверах](../../../relational-databases/security/encryption/create-identical-symmetric-keys-on-two-servers.md)  
  
 [Enable TDE on SQL Server Using EKM (Включение прозрачного шифрования данных в SQL Server с помощью расширенного управления ключами)](../../../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)  
  
 [Расширенное управление ключами с помощью хранилища ключей Azure (SQL Server)](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
 [Шифрование столбца данных](../../../relational-databases/security/encryption/encrypt-a-column-of-data.md)  
  
## <a name="related-content"></a>См. также  
 [CREATE MASTER KEY (Transact-SQL)](../../../t-sql/statements/create-master-key-transact-sql.md)  
  
 [ALTER SERVICE MASTER KEY (Transact-SQL)](../../../t-sql/statements/alter-service-master-key-transact-sql.md)  
  
 [Восстановление главного ключа базы данных](../../../relational-databases/security/encryption/restore-a-database-master-key.md)  
  
## <a name="see-also"></a>См. также:  
 [Резервное копирование и восстановление ключей шифрования служб Reporting Services](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)   
 [Удаление и повторное создание ключей шифрования (диспетчер конфигурации служб SSRS)](../../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)   
 [Добавление и удаление ключей шифрования для масштабного развертывания (диспетчер конфигурации служб SSRS)](../../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md)   
 [Прозрачное шифрование данных (TDE)](../../../relational-databases/security/encryption/transparent-data-encryption.md)  
  
  
