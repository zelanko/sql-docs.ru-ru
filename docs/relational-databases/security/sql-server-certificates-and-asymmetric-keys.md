---
title: Сертификаты и асимметричные ключи в SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: security
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server], certificates and asymmetric keys
ms.assetid: 8519aa2f-f09c-4c1c-96b5-abc24811e60c
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2875295c5978f54dcff3ee2b5a5129db36757f7a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sql-server-certificates-and-asymmetric-keys"></a>Сертификаты SQL Server и асимметричные ключи
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Криптография с открытым ключом представляет собой форму обеспечения конфиденциальности сообщений, подразумевающую создание *открытого* и *закрытого* ключей. Закрытый ключ хранится в секрете, а открытый ключ передается другим лицам. Хотя ключи математически связаны, закрытый ключ нельзя легко вычислить с помощью открытого ключа. Открытый ключ используется при шифровании данных, а закрытый ключ используется при расшифровке данных. Сообщение, зашифрованное с помощью открытого ключа, можно расшифровать только с помощью правильного закрытого ключа. Поскольку применяются два различных ключа, эти ключи *асимметричные*.  
  
 Как сертификаты, так и асимметричные ключи представляют собой способы асимметричного шифрования. Сертификаты часто используются как контейнеры для асимметричных ключей, так как они могут содержать дополнительные данные, например о датах окончания действия и поставщиках. Не существует различий между двумя механизмами для алгоритма шифрования, равно как и различий в надежности при одинаковой длине ключа. Как правило, сертификат используется для шифрования других типов ключей шифрования в базе данных, или подписи программных модулей.  
  
 Сертификаты и асимметричные ключи можно применять для расшифровки данных, зашифрованных другим способом. Обычно асимметричный ключ используется для шифрования симметричного ключа перед его сохранением в базе данных.  
  
 В отличие от сертификата, открытый ключ не имеет определенного формата, и его нельзя экспортировать в файл.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет функции, которые позволяют создавать сертификаты и ключи для использования с сервером и базой данных, а также управлять этими сертификатами и ключами. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] нельзя использовать для создания сертификатов и ключей (и управления сертификатами и ключами) с другими приложениями или в операционной системе.  
  
## <a name="certificates"></a>Сертификаты  
 Сертификат представляет собой объект безопасности с цифровой подписью, который содержит открытый (и необязательно закрытый) ключ для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Можно использовать сертификаты, сформированные внешними средствами, или сертификаты, созданные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Сертификаты соответствуют стандарту сертификатов IETF X.509v3.  
  
 Сертификаты полезны благодаря возможности выполнить как экспорт ключей в файлы сертификатов X.509, так и импорт из них. Синтаксис, применяемый при создании сертификатов, позволяет вводить параметры создания для сертификатов, например дату окончания действия.  
  
### <a name="using-a-certificate-in-sql-server"></a>Использование сертификата в SQL Server  
 Сертификаты могут использоваться для защиты соединений, при зеркальном отображении баз данных, подписывании пакетов и других объектов, шифровании данных или соединений. В следующей таблице перечислены дополнительные ресурсы для сертификатов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Раздел|Description|  
|-----------|-----------------|  
|[CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)|Содержит описание команды создания сертификатов.|  
|[Определение источника пакетов с помощью цифровых подписей](../../integration-services/security/identify-the-source-of-packages-with-digital-signatures.md)|Содержит сведения об использовании сертификатов для подписывания программных пакетов.|  
|[Использование сертификатов для конечной точки зеркального отображения базы данных (Transact-SQL)](../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)|Содержит сведения об использовании сертификатов с зеркальным отображением базы данных.|  
  
## <a name="asymmetric-keys"></a>Асимметричные ключи  
 Асимметричные ключи используются для защиты симметричных ключей. Их можно также использовать для ограниченного шифрования данных и цифрового подписывания объектов базы данных. Асимметричный ключ состоит из закрытого ключа и соответствующего открытого ключа. Дополнительные сведения об асимметричных ключах см. в разделе [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md).  
  
 Асимметричные ключи можно импортировать из файлов ключа для строгого имени, но их нельзя экспортировать. Они также не имеют даты окончания действия. Асимметричные ключи нельзя применять для шифрования соединений.  
  
### <a name="using-an-asymmetric-key-in-sql-server"></a>Использование асимметричного ключа в SQL Server  
 Асимметричные ключи можно использовать для защиты данных или подписывания незашифрованного текста. В следующей таблице перечислены дополнительные ресурсы для асимметричных ключей в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Раздел|Description|  
|-----------|-----------------|  
|[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)|Содержит описание команды создания асимметричных ключей.|  
|[SIGNBYASYMKEY (Transact-SQL)](../../t-sql/functions/signbyasymkey-transact-sql.md)|Отображает параметры для подписывания объектов.|  
  
## <a name="tools"></a>Инструменты  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] предоставляет средства и программы, которые создают сертификаты и файлы ключа для строгого имени. Эти средства обеспечивают более гибкий процесс создания ключа, чем синтаксис [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . С помощью этих средств можно создать ключи RSA большей длины, а затем импортировать их в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В следующей таблице показано, где найти эти средства.  
  
|||  
|-|-|  
|Инструмент|Назначение|  
|[makecert](http://msdn2.microsoft.com/library/bfsktky3\(VS.80\).aspx)|Создает сертификаты.|  
|[sn](http://msdn2.microsoft.com/library/k5b5tt23\(VS.80\).aspx)|Создает строгие имена для симметричных ключей.|  
  
## <a name="related-tasks"></a>Related Tasks  
 [Выбор алгоритма шифрования](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)  
  
 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [sys.certificates (Transact-SQL)](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)   
 [Прозрачное шифрование данных (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md)  
  
  
