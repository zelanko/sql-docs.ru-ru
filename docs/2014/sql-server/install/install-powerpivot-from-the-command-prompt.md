---
title: Установка PowerPivot из командной строки | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 7f1f2b28-c9f5-49ad-934b-02f2fa6b9328
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 8959b1ca4ea719ce571cb8609b817bba965185bd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "72798327"
---
# <a name="install-powerpivot-from-the-command-prompt"></a>Установка PowerPivot из командной строки
  Программу установки SQL Server PowerPivot для SharePoint можно запустить из командной строки. В команду необходимо включить параметр `/ROLE` и исключить из нее параметр `/FEATURES`.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Необходимо установить выпуск SharePoint Server 2010 Enterprise Edition с пакетом обновления 1 (SP1).  
  
 Для подготовки к работе служб Analysis Services необходимо использовать учетные записи пользователей домена.  
  
 Компьютер должен быть присоединен к тому же домену, что и ферма SharePoint.  
  
##  <a name="Commands"></a>Параметры установки на основе/ROLE  
 При развертывании PowerPivot для SharePoint используется параметр `/ROLE` вместо параметра `/FEATURES`. Допустимые значения:  
  
-   `SPI_AS_ExistingFarm`  
  
-   `SPI_AS_NewFarm`  
  
 При использовании обеих ролей устанавливаются файлы приложения, конфигурации и развертывания, позволяющие PowerPivot для SharePoint работать в ферме SharePoint. При выборе любой роли программа установки проверит соответствие требованиям к программному и аппаратному обеспечению, которые должны быть удовлетворены для интеграции с SharePoint.  
  
 Параметр «Существующая ферма» предполагает, что ферма SharePoint уже сконфигурирована. При выборе варианта Новая ферма предполагается, что вы создадите новую ферму. Он поддерживает добавление ядро СУБД экземпляра в синтаксисе командной строки, чтобы можно было использовать экземпляр ядро СУБД в качестве сервера базы данных фермы.  
  
 В отличие от предыдущих выпусков, все задачи настройки сервера выполняются как задачи после установки. В целях автоматизации шагов по установке и настройке для настройки сервера можно использовать PowerShell. Дополнительные сведения см. в статье [Настройка PowerPivot с помощью Windows PowerShell](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell).  
  
## <a name="example-commands"></a>Примеры команд  
 В следующих примерах демонстрируется применение каждого из вариантов. В примере 1 `SPI_AS_ExistingFarm`показано.  
  
```cmd
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_ExistingFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 Пример 2 иллюстрирует вариант `SPI_AS_NewFarm`. Обратите внимание, что он включает параметры для провизионирования компонента Database Engine.  
  
```cmd
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_NewFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/SQLSVCACCOUNT=<DomainName\UserName> /SQLSVCPASSWORD=<StrongPassword> /SQLSYSADMINACCOUNTS=<DomainName\UserName> /AGTSVCACCOUNT=<DomainName\UserName> /AGTSVCPASSWORD=<StrongPassword> /ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
##  <a name="Join"></a>Изменение синтаксиса команды  
 Используйте следующие шаги для изменения примера синтаксиса команды.  
  
1.  Скопируйте следующую команду в Блокнот:  
  
    ```cmd
    Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_ExistingFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
    ```  
  
     Параметр `/q` запускает программу установки в «тихом» режиме, в котором пользовательский интерфейс не задействуется.  
  
     Когда параметр `/IAcceptSQLServerLicenseTerms` или `/q` задан для автоматических установок, требуется `/qs`.  
  
     Параметр `/action` дает указание программе установки выполнить установку.  
  
     Параметр `/role` дает указание программе установки установить службы Analysis Services и файлы конфигурации, необходимые для работы PowerPivot для SharePoint. Эта роль также определяет и использует сведения о соединении существующей фермы для доступа к базе данных конфигурации SharePoint. Это обязательный параметр. Используйте его вместо параметра `/features`, чтобы указать компоненты для установки.  
  
     Параметр `/instancename` указывает «PowerPivot» в качестве именованного экземпляра. Это значение задано жестко, его невозможно изменить. Оно указывается в команде в образовательных целях с тем, чтобы пользователь знал, как устанавливается служба.  
  
     С помощью параметра `/indicateprogress` можно отслеживать ход выполнения в окне командной строки.  
  
2.  Параметр `PID` в команде не указывается, в результате чего устанавливается выпуск Evaluation. Если требуется установить выпуск Enterprise Edition, добавьте параметр PID в команду запуска программы установки и укажите действительный ключ продукта.  
  
    ```  
    /PID=<product key for an Enterprise installation>  
    ```  
  
3.  Замените заполнители для \<домен \ имя_пользователя> \<и StrongPassword>действительными учетными записями пользователей и паролями.  
  
     Параметры `/assvaccount` и **/ассвкпассворд** используются для настройки [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] экземпляра на сервере приложений. Замените эти заполнители на допустимые сведения учетной записи.  
  
     Для параметра **/ассисадминаккаунтс** необходимо задать идентификатор пользователя, выполняющего программу установки SQL Server. Для служб необходимо указать хотя бы одного системного администратора. Следует отметить, что программа установки SQL Server больше не предоставляет автоматически разрешения sysadmin членам встроенной группы «Администраторы».  
  
4.  Удалите разрывы строк.  
  
5.  Выделите всю команду и выберите команду **Копировать** в меню Правка.  
  
6.  Откройте командную строку администратора. Для этого нажмите кнопку **Пуск**, щелкните правой кнопкой мыши командную строку и выберите **Запуск от имени администратора**.  
  
7.  Перейдите в папку на диске или общую папку, которая содержит установочный носитель SQL Server.  
  
8.  Вставьте измененную команду в командную строку. Для этого щелкните значок в левом верхнем углу окна командной строки, наведите указатель мыши на пункт **изменить**и выберите команду **Вставить**.  
  
9. Нажмите клавишу **Ввод** , чтобы выполнить команду. Подождите завершения работы программы установки. В окне командной строки можно наблюдать за ходом выполнения.  
  
10. Чтобы проверить установку, в папке \Program Files\SQL Server\120\Setup Bootstrap\Log откройте файл summary.txt. Если сервер был установлен без ошибок, то окончательный результат должен содержать текст «Выполнено».  
  
11. Настройте сервер. Как минимум необходимо развернуть решения, создать приложение службы и включить этот компонент для каждого семейства веб-сайтов. Дополнительные сведения см. в статьях [Настройка или восстановление PowerPivot для SharePoint 2010 &#40;средства настройки powerpivot&#41;](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md) или [Администрирование сервера PowerPivot и настройка в центре администрирования](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration).  
  
## <a name="see-also"></a>См. также:  
 [Настройка учетных записей служб PowerPivot](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts)   
 [Установка PowerPivot для SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
