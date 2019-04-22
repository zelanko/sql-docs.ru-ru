---
title: Шифрование в SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], about encryption
- security [SQL Server], encryption
- cryptography [SQL Server], about cryptography
ms.assetid: ead0150e-4943-4ad5-84c8-36f85c7278f4
author: aliceku
ms.author: aliceku
manager: craigg
ms.openlocfilehash: 1484a32eb808e6778896a498d5a6dee525b18aed
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59242462"
---
# <a name="sql-server-encryption"></a>Шифрование SQL Server
  Шифрование представляет собой способ скрытия данных с помощью ключа или пароля. Это делает данные бесполезными без соответствующего ключа или пароля для дешифрования. Шифрование не решает проблемы управления доступом. Однако оно повышает защиту за счет ограничения потери данных даже при обходе системы управления доступом. Например, если компьютер, на котором установлена база данных, был настроен неправильно и злоумышленник смог получить конфиденциальные данные, то украденная информация будет бесполезна, если она была предварительно зашифрована.  
  
 В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] можно шифровать соединения, данные и хранимые процедуры. В следующей таблице содержатся дополнительные сведения о шифровании в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Несмотря на то, что шифрование является полезным средством обеспечения безопасности, его не следует применять ко всем данным или соединениям. При решении о внедрении шифрования необходимо проанализировать, как пользователи получают доступ к данным. Если пользователи получают доступ к данным через открытую сеть, то шифрование может потребоваться для повышения безопасности. Однако если весь доступ осуществляется по безопасной внутренней сети, то шифрование не требуется. Использование шифрования включает политику управления паролями, ключами и сертификатами.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Иерархия средств шифрования](encryption-hierarchy.md)  
 Сведения об иерархии шифрования в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Выбор алгоритма шифрования](choose-an-encryption-algorithm.md)  
 Сведения о выборе эффективного алгоритма шифрования.  
  
 [Прозрачное шифрование данных (TDE)](transparent-data-encryption.md)  
 Общие сведения о прозрачном шифровании данных.  
  
 [Ключи шифрования базы данных и SQL Server (компонент Database Engine)](sql-server-and-database-encryption-keys-database-engine.md)  
 Используемые в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ключи шифрования представляют собой сочетание открытых, закрытых и симметричных ключей, которые используются для защиты конфиденциальных данных. В этом разделе рассказывается о внедрении и управлении ключами шифрования.  
  
## <a name="related-content"></a>См. также  
 [Обеспечение безопасности SQL Server](../securing-sql-server.md)  
 Общие сведения о способах обеспечения безопасности платформы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и способах работы с пользователями и защищаемыми объектами.  
  
 [Криптографические функции (Transact-SQL)](/sql/t-sql/functions/cryptographic-functions-transact-sql)  
 Сведения о внедрении криптографических функций.  
  
 [ENCRYPTBYPASSPHRASE (Transact-SQL)](/sql/t-sql/functions/encryptbypassphrase-transact-sql)  
 Сведения об использовании паролей для шифрования данных.  
  
 [ENCRYPTBYKEY (Transact-SQL)](/sql/t-sql/functions/encryptbykey-transact-sql)  
 Сведения об использовании симметричных ключей для шифрования данных.  
  
 [ENCRYPTBYASYMKEY (Transact-SQL)](/sql/t-sql/functions/encryptbyasymkey-transact-sql)  
 Сведения об использовании асимметричных ключей для шифрования данных.  
  
 [ENCRYPTBYCERT (Transact-SQL)](/sql/t-sql/functions/encryptbycert-transact-sql)  
 Сведения об использовании сертификатов для шифрования данных.  
  
## <a name="external-resources"></a>Внешние ресурсы  
 [10 шагов к безопасности SQL Server 2005](https://www.itprotoday.com/sql-server/10-steps-sql-server-2005-security)  
 Текущие сведения о безопасности в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [sys.key_encryptions (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-key-encryptions-transact-sql)   
 [Ключи шифрования базы данных и SQL Server (компонент Database Engine)](sql-server-and-database-encryption-keys-database-engine.md)   
 [Резервное копирование и восстановление ключей шифрования служб Reporting Services](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)  
  
  
