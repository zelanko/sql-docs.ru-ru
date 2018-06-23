---
title: Обновление до другого выпуска SQL Server 2014 (программа установки) | Документы Microsoft
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31d16820-d126-4c57-82cc-27701e4091bc
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8f2b3739bf23e2e7405d95e856df7e776e498709
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190596"
---
# <a name="upgrade-to-a-different-edition-of-sql-server-2014-setup"></a>обновить SQL Server 2014 до другого выпуска (программа установки)
  Программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает обновление различных выпусков [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Сведения о поддерживаемых способах обновления выпуска см. в разделе [Поддерживаемые обновления выпусков и версий](supported-version-and-edition-upgrades.md). Прежде чем начать обновление выпуска экземпляра [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], ознакомьтесь со следующими разделами.  
  
-   [Возможности, поддерживаемые различными выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
-   [Выпуски и компоненты SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md)  
  
-   [Ограничения по производительности вычислений для разных выпусков SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)  
  
-   [Требования к оборудованию и программному обеспечению для установки SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
> [!NOTE]  
>  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в кластерной среде.** Достаточно обновить выпуск на одном из узлов кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Этот узел может быть как активным, так и пассивным, а ядро не переводит ресурсы в автономный режим во время обновления выпуска. После обновления выпуска требуется либо перезапустить экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо переключиться на другой узел.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для локальных установок необходимо запускать программу установки с правами администратора. Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливается с удаленного общего ресурса, необходимо использовать учетную запись домена, у которой есть разрешения на чтение на этом удаленном ресурсе.  
  
> [!IMPORTANT]  
>  Чтобы активировать изменения выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо перезапустить службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Нахождение служб в режиме «вне сети» приведет к простою приложений.  
  
## <a name="procedure"></a>Процедура  
  
#### <a name="to-upgrade-to-a-different-edition-of-includesscurrentincludessscurrent-mdmd"></a>Обновление до другого выпуска [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
1.  Вставьте установочный носитель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В корневой папке дважды щелкните файл setup.exe или запустите центр установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из средств настройки. Чтобы выполнить установку из общей сетевой папки, перейдите в корневую папку общего ресурса и дважды щелкните файл setup.exe.  
  
2.  Чтобы обновить существующий экземпляр [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] до другого выпуска, в центре установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выберите **Обслуживание**, затем выберите **Обновить выпуск**.  
  
3.  Если требуются файлы поддержки программы установки, программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установит их. Если будет предложено перезагрузить компьютер, перезапустите его перед продолжением.  
  
4.  Средство проверки конфигурации системы запускает операцию обнаружения на компьютере. Чтобы продолжить, нажмите кнопку **ОК**.  
  
5.  На странице «Ключ продукта» щелкните переключатель, чтобы определить, обновлять до бесплатного выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]или имеется ключ PID для рабочей версии продукта. Дополнительные сведения см. в разделе [выпуски и компоненты SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) и [Supported Version and Edition Upgrades](supported-version-and-edition-upgrades.md).  
  
6.  На странице «Условия лицензии» прочтите лицензионное соглашение, а затем установите флажок, подтверждая принятие условий соглашения. Чтобы продолжить, нажмите кнопку **Далее**. Чтобы выйти из программы установки, нажмите кнопку **Отмена**.  
  
7.  На странице «Выбор экземпляра» укажите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который необходимо обновить.  
  
8.  Конфигурация компьютера проверяется на странице «Правила обновления выпуска» перед началом операции обновления выпуска.  
  
9. На странице «Все готово для обновления выпуска» показано представление параметров установки в виде дерева, выбранных в программе установки. Чтобы продолжить, нажмите кнопку **Обновить**.  
  
10. В процессе обновления выпуска необходимо перезапустить службы, чтобы применить новую настройку. После обновления выпуска на завершающей странице содержится ссылка на файл сводного журнала установки для обновления выпуска. Чтобы завершить работу мастера, нажмите кнопку **Закрыть**.  
  
11. На завершающей странице содержится ссылка на файл сводного журнала установки и другие важные примечания.  
  
12. Если будет предложено перезагрузить компьютер, выполните перезагрузку. После завершения установки важно прочитать сообщение мастера установки. Дополнительные сведения о файлах журналов установки см. в разделе [Просмотр и чтение файлов журналов программы установки SQL Server](view-and-read-sql-server-setup-log-files.md).  
  
13. При обновлении с версии [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]перед использованием обновленного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]необходимо выполнить дополнительные шаги.  
  
    -   Включить службу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в Windows SCM.  
  
    -   Назначить учетную запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 В дополнение к приведенным выше шагам, возможно, потребуется выполнить следующие действия, если выполняется обновление с версии [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].  
  
-   Пользователи, заданные в [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] , не изменяются. В частности, группа пользователей BUILTIN\Users сохраняется. При необходимости отключите, удалите или переназначьте эти учетные записи. Дополнительные сведения см. в статье [Настройка учетных записей службы Windows и разрешений](../configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
-   Размеры и режим восстановления для системных баз данных tempdb и model после обновления остаются неизменными. При необходимости измените эти настройки. Дополнительные сведения см. в статье [Резервное копирование и восстановление системных баз данных (SQL Server)](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md).  
  
-   Шаблоны баз данных остаются на компьютере после обновления.  
  
## <a name="see-also"></a>См. также  
 [Обновление до SQL Server 2014](upgrade-sql-server.md)   
 [Обратная совместимость](../../getting-started/backward-compatibility.md)  
  
  