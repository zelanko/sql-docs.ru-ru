---
ms.openlocfilehash: 4803a99e0fb1435b545ec775b2a8abe063d9fd8d
ms.sourcegitcommit: cbbb210c0315f9e2be2b9cd68db888ac53429814
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2019
ms.locfileid: "69890919"
---
Учетная запись **системного администратора** (SA) обладает правами администратора на экземпляре SQL Server, создаваемом во время установки. После создания контейнера SQL Server указанную вами переменную среды `MSSQL_SA_PASSWORD` можно обнаружить, запустив `echo $MSSQL_SA_PASSWORD` в контейнере. В целях безопасности смените пароль системного администратора.

1. Назначьте для пользователя SA надежный пароль.

1. Используйте `docker exec` для запуска программы **sqlcmd**, чтобы изменить пароль с помощью инструкции Transact-SQL. Замените `<YourStrong!Passw0rd>` и `<YourNewStrong!Passw0rd>` собственными значениями пароля.

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourStrong!Passw0rd>' \
      -Q 'ALTER LOGIN SA WITH PASSWORD="<YourNewStrong!Passw0rd>"'
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourStrong!Passw0rd>" `
      -Q "ALTER LOGIN SA WITH PASSWORD='<YourNewStrong!Passw0rd>'"
   ```
