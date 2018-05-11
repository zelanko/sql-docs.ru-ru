---
title: Вопросы безопасности при установке SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: install
ms.reviewer: ''
ms.suite: sql
ms.technology:
- setup-install
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- firewall systems [SQL Server]
- server message blocks [SQL Server]
- disabling protocols
- security [SQL Server], installations
- protocols [SQL Server], disabling
- NetBIOS [SQL Server]
- services [SQL Server], security
- SMB [SQL Server]
- isolating services [SQL Server]
- Setup [SQL Server], security
- low SQL Server installation privileges
- NTFS [SQL Server]
- physical security [SQL Server]
- file system security [SQL Server]
- installing SQL Server, security
ms.assetid: cf96155f-30a8-48b7-8d6b-24ce90dafdc7
caps.latest.revision: 48
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: daeecfae419ca6a94ba3d986bf8c4b8e3bb18e1f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="security-considerations-for-a-sql-server-installation"></a>Вопросы безопасности при установке SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

 Безопасность является важной характеристикой для любого продукта и любого предприятия. Следуя простым рекомендациям, можно избежать многих уязвимостей в безопасности. В этой статье обсуждаются некоторые рекомендации по безопасности, которых следует придерживаться как до установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], так и после установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о безопасности для конкретных компонентов приводятся в справочных статьях по этим компонентам.  
  
## <a name="before-installing-includessnoversionincludesssnoversion-mdmd"></a>Перед установкой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 При настройке среды сервера выполняйте следующие рекомендации.  
  
-   [Повышение физической безопасности](#physical_security)  
  
-   [Использование брандмауэров](#firewalls)  
  
-   [Изолирование служб](#isolated_services)  
  
-   [Настройка безопасной файловой системы](#sa_with_least_privileges)  
  
-   [Отключение протоколов NetBIOS и SMB](#disabled_protocols)  
  
-   [Установка SQL Server на контроллере домена](../../sql-server/install/security-considerations-for-a-sql-server-installation.md#Install_DC)  
  
###  <a name="physical_security"></a> Enhance Physical Security  
 Физическая и логическая изоляции составляют основу безопасности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для повышения физической безопасности установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполните следующие действия.  
  
-   Установите сервер в помещении, недоступном для посторонних.  
  
-   Установите компьютеры, на которых размещены базы данных, в физически защищенных местах, идеальным вариантом является запертая компьютерная комната с системой электромагнитного и противопожарного контроля или системой подавления помех.  
  
-   Установите базы данных в безопасной зоне корпоративной сети и не подключайте экземпляры SQL Server к Интернету напрямую.  
  
-   Регулярно создавайте резервные копии данных и храните их в безопасном месте за пределами расположения компьютера.  
  
###  <a name="firewalls"></a> Use Firewalls  
 Брандмауэры играют важную роль в обеспечении безопасности установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Брандмауэры будут более эффективны, если следовать приведенным ниже правилам.  
  
-   Установите брандмауэр между сервером и Интернетом. Разрешите работу брандмауэра. Если он отключен, включите его. Если он включен, не отключайте.  
  
-   Разделите сеть на зоны безопасности, разделенные брандмауэрами. Заблокируйте весь поток данных, после чего разрешите только необходимый.  
  
-   В многоуровневой архитектуре используйте несколько брандмауэров для создания изолированных подсетей.  
  
-   При установке сервера внутри домена Windows настройте внутренние брандмауэры на разрешение проверки подлинности Windows.  
  
-   Если приложение работает с распределенными транзакциями, настройте брандмауэр на обмен данными между отдельными экземплярами координатора распределенных транзакций [!INCLUDE[msCoName](../../includes/msconame-md.md)] (MS DTC). Кроме того, нужно настроить брандмауэр на разрешение обмена данными между MS DTC и диспетчерами ресурсов (например, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]).  
  
 Дополнительные сведения о настройках брандмауэра Windows по умолчанию и описание портов TCP, влияющих на компоненты [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]и [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], см. в разделе [Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
###  <a name="isolated_services"></a> Isolate Services  
 Изолирование служб уменьшает риск того, что подвергнувшаяся опасности служба подвергнет опасности другие службы. Чтобы изолировать службы, следуйте приведенным ниже правилам.  
  
-   Запускайте разные службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под разными учетными записями Windows. Если возможно, пользуйтесь для каждой из служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отдельными учетными записями Windows или локальных пользователей, обладающих наименьшими правами. Дополнительные сведения см. в статье [Настройка учетных записей службы Windows и разрешений](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
###  <a name="sa_with_least_privileges"></a> Configure a Secure File System  
 Правильный выбор файловой системы повышает уровень безопасности. Для установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо выполнить следующие действия.  
  
-   Используйте файловую систему NTFS. Рекомендуется устанавливать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на файловую систему NTFS, так как она обеспечивает более высокую стабильность и восстанавливаемость, чем файловые системы FAT. Кроме того, NTFS реализует параметры управления доступом к файлам и каталогам (ACL), шифрование файловой системы (EFS) и другие средства обеспечения безопасности. Во время установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установит необходимые списки ACL на разделы реестра и файлы, если программа установки обнаружит NTFS. Эти разрешения не должны меняться. В будущих выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может не поддерживаться установка на компьютеры с файловой системой FAT.  
  
    > [!NOTE]  
    >  При использовании EFS файлы базы данных будут зашифрованы идентификатором учетной записи, под которой запущен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Только эта учетная запись сможет расшифровать файлы. Если нужно изменить учетную запись, от имени которой запускается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сначала необходимо расшифровать файлы с использованием старой учетной записи, а затем снова зашифровать их под новой учетной записью.  
  
-   Используйте дисковый массив (RAID) для наиболее критичных файлов данных.  
  
###  <a name="disabled_protocols"></a> Disable NetBIOS and Server Message Block  
 На внешних серверах сети должны быть отключены все ненужные протоколы, включая NetBIOS и SMB.  
  
 NetBIOS использует следующие порты:  
  
-   UDP/137 (служба имен NetBIOS);  
  
-   UDP/138 (служба дейтаграмм NetBIOS);  
  
-   UDP/139 (служба сеанса NetBIOS).  
  
 SMB использует следующие порты:  
  
-   TCP/139  
  
-   TCP/445  
  
 Веб-серверы и DNS-серверы не требуют наличия NetBIOS или SMB. Отключите на них оба протокола, чтобы снизить угрозу раскрытия списка пользователей.  
  
###  <a name="Install_DC"></a> Установка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на контроллере домена  
 Исходя из соображений безопасности, не рекомендуется устанавливать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на контроллере домена. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не заблокирует установку на компьютере, который является контроллером домена, однако при этом будут применены следующие ограничения.  
  
-   Запуск служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на контроллере домена в учетной записи локальной службы невозможен.  
  
-   После установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютер, который является членом домена, нельзя будет сделать контроллером домена. Перед этим придется удалить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   После установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютер, который является контроллером домена, нельзя будет сделать членом домена. Перед этим придется удалить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает экземпляры отказоустойчивого кластера, где узлы кластера являются контроллерами домена.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Программа установки не может создавать группы безопасности или подготавливать учетные записи служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на контроллере домена, доступном только для чтения. В такой ситуации программа установки завершается ошибкой.  
  
## <a name="during-or-after-installation-of-includessnoversionincludesssnoversion-mdmd"></a>Во время или после установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 После установки вы можете повысить безопасность установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , следуя приведенным ниже рекомендациям относительно учетных записей и режимов проверки подлинности.  
  
 **Учетные записи службы**  
  
-   Запускайте службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с минимально возможными разрешениями.  
  
-   Связывайте службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с учетными записями локальных пользователей Windows, имеющих наименьшие права доступа, или учетными записями пользователей домена.  
  
-   Дополнительные сведения см. в разделе [Настройка учетных записей службы Windows и разрешений](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
 **Режим проверки подлинности**  
  
-   Требует проверку подлинности Windows для подключений к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Используйте проверку подлинности Kerberos. Дополнительные сведения см. в разделе [Регистрация имени участника-службы для соединений Kerberos](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).  
  
 **Надежные пароли**  
  
-   Всегда назначайте надежный пароль для учетной записи **sa** .  
  
-   Всегда включайте проверку политики паролей для определения надежности и срока действия пароля.  
  
-   Для всех имен входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используйте только надежные пароли.  
  
> [!IMPORTANT]  
>  Во время установки [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] для группы BUILTIN\Users добавляется имя входа. Благодаря этому все прошедшие проверку подлинности пользователи компьютера получают доступ к экземпляру [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] как члены роли public. Имя входа группы BUILTIN\Users можно удалить, чтобы ограничить доступ к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)] только пользователям компьютера, у которых есть отдельные имена входа, или членам других групп Windows с именами входа.  
  
## <a name="see-also"></a>См. также:  
 [Требования к оборудованию и программному обеспечению для установки SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)   
 [Сетевые протоколы и библиотеки](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [Регистрация имени участника-службы для соединений Kerberos](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)  
  
  
