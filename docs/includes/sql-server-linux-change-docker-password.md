---
ms.openlocfilehash: 70c86c40f290c26db5bcbc3526d66466c20504d8
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68214884"
---
Учетная запись **SA** обладает правами администратора на экземпляре SQL Server, создаваемом во время установки. После создания контейнера SQL Server указанную вами переменную среды `MSSQL_SA_PASSWORD` можно обнаружить, запустив `echo $MSSQL_SA_PASSWORD` в контейнере. В целях безопасности смените пароль SA.

1. Назначьте для пользователя SA надежный пароль.

1. Используйте `docker exec` для запуска **sqlcmd**, чтобы изменить пароль с помощью Transact-SQL. Замените `<YourStrong!Passw0rd>` и `<YourNewStrong!Passw0rd>` собственными значениями пароля.

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
