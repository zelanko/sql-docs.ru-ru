---
title: "Выбор алгоритма шифрования | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/08/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cryptography [SQL Server], algorithms
- encryption [SQL Server], algorithms
- security [SQL Server], encryption
- algorithms [SQL Server encryption]
ms.assetid: 8227028c-a9c9-489d-bd27-fbf8242634ae
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 7b4f037616e0559ac62bbae5dbe04aeffe529b06
ms.openlocfilehash: 77cee9391335f384c94aa0fa3cf71808baf36056
ms.contentlocale: ru-ru
ms.lasthandoff: 08/28/2017

---
# <a name="choose-an-encryption-algorithm"></a>Выбор алгоритма шифрования
  Шифрование — одно из нескольких эффективных средств защиты, позволяющих администраторам обеспечивать безопасность экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Алгоритмы шифрования определяют преобразования данных, исключающие возможность легкого восстановления исходного текста неавторизированными пользователями. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] позволяет администраторам и разработчикам выбирать из нескольких алгоритмов, в том числе DES, Triple DES, TRIPLE_DES_3KEY, RC2, RC4, RC4 со 128-разрядным ключом, DESX, AES со 128-разрядным ключом, AES со 192-разрядным ключом и AES с 256-разрядным ключом.  
  
> [!NOTE]  
>  Начиная с версии [!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)]все алгоритмы, отличные от AES_128, AES_192 и AES_256, являются нерекомендуемыми. Чтобы использовать старые алгоритмы (что не рекомендуется), необходимо установить уровень совместимости базы данных 120 или ниже.  
  
 Не существует одного алгоритма, идеально подходящего для всех случаев. Информация по качеству каждого из них лежит за пределами электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Однако можно руководствоваться следующими общими принципами:  
  
-   Надежные алгоритмы шифрования обычно потребляют больше ресурсов ЦП, чем менее надежные средства шифрования.  
  
-   Использование длинных ключей, как правило, дает более надежные результаты, чем шифрование с помощью коротких ключей.  
  
-   Асимметричное шифрование слабее симметричного шифрования с использованием ключа той же длины, но является относительно медленным.  
  
-   Блочные шифры с длинными ключами надежнее поточных шифров.  
  
-   Длинные сложные пароли надежнее, чем короткие пароли.  
  
-   При необходимости шифровать большие объемы данных, шифруйте данные с помощью симметричного ключа, а симметричный ключ — с помощью асимметричного ключа.  
  
-   Зашифрованные данные не поддаются сжатию, но сжатые данные могут быть зашифрованы. При использовании сжатия данных, выполняйте эту операцию до их шифрования.  
  
> [!IMPORTANT]  
>  Алгоритм RC4 поддерживается только в целях обратной совместимости. Когда база данных имеет уровень совместимости 90 или 100, новые материалы могут шифроваться только с помощью алгоритмов RC4 или RC4_128. (Не рекомендуется.) Используйте вместо этого более новые алгоритмы, например AES. В [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] и более поздних версиях материалы, зашифрованные с помощью алгоритмов RC4 или RC4_128, могут быть расшифрованы на любом уровне совместимости.  
>   
>  Многократное использование одного и того же RC4 или RC4_128 KEY_GUID для различных блоков данных приведет к одному и тому же ключу RC4, так как [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не предоставляет рассеивание автоматически. Повторное использование ключа RC4 является типичной ошибкой, снижающей надежность шифра. Таким образом, ключевые слова RC4 и RC4_128 являются устаревшими. [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)]  
  
 Дополнительные сведения об алгоритмах шифрования и о технологии шифрования см. в разделе [Основные понятия безопасности](http://go.microsoft.com/fwlink/?LinkId=62082) руководства разработчика для платформы .NET Framework в сети MSDN.  
  
 **Пояснение к алгоритмам DES:**  
  
-   DESX был именован неправильно. Симметричные ключи, созданные с параметром ALGORITHM = DESX, в действительности используют шифр TRIPLE DES с 192-битным ключом. Алгоритм DESX не предоставляется. [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
-   Симметричные ключи, созданные с параметром ALGORITHM = TRIPLE_DES_3KEY, используют шифр TRIPLE DES с 192-битным ключом.  
  
-   Симметричные ключи, созданные с параметром ALGORITHM = TRIPLE_DES, используют шифр TRIPLE DES с 128-битным ключом.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|||  
|-|-|  
|Шифрование с помощью симметричного ключа.|[CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-symmetric-key-transact-sql.md)|  
|Шифрование с помощью асимметричного ключа.|[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-asymmetric-key-transact-sql.md)|  
|Кодирование с использованием сертификата.|[CREATE CERTIFICATE (Transact-SQL)](../../../t-sql/statements/create-certificate-transact-sql.md)|  
|Шифрование файлов базы данных с помощью прозрачного шифрования данных.|[Прозрачное шифрование данных (TDE)](../../../relational-databases/security/encryption/transparent-data-encryption.md)|  
|Как зашифровать столбец таблицы.|[Шифрование столбца данных](../../../relational-databases/security/encryption/encrypt-a-column-of-data.md)|  
  
## <a name="see-also"></a>См. также:  
 [Шифрование SQL Server](../../../relational-databases/security/encryption/sql-server-encryption.md)   
 [Иерархия средств шифрования](../../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

