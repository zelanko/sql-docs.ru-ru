---
title: Установка SQL Server 2014 с помощью файла конфигурации | Документация Майкрософт
ms.custom: ''
ms.date: 01/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: a832153a-6775-4bed-83f0-55790766d885
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 38cd8aeb157a94a28b1cfd831bcfacfb3e93ea6f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62775287"
---
# <a name="install-sql-server-2014-using-a-configuration-file"></a>установить SQL Server 2014 с помощью файла конфигурации
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Программа установки предоставляет возможность создать файл конфигурации на основе системных значений по умолчанию и значений, вводимых во время выполнения. Файл конфигурации может быть использован для развертывания [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на всем предприятии с одной и той же конфигурацией. Стандартизировать установки в ручном режиме на территории предприятия также можно, создав пакетный файл, запускающий файл Setup.exe.  
  
 Программа установки поддерживает использование файлов конфигурации только через командную строку. Порядок обработки параметров при использовании файла конфигурации описывается ниже.  
  
-   Файл конфигурации перезаписывает значения по умолчанию в пакете.  
  
-   Значения командной строки перезаписывают значения в файле конфигурации.  
  
 Файл конфигурации может быть использован для нахождения параметров и значений для каждой установки. В связи с этим файл конфигурации может быть полезен при проверке и аудите установок.  
  
## <a name="configuration-file-structure"></a>Структура файла конфигурации  
 Файл ConfigurationFile.ini — это текстовый файл с параметрами (пара «имя-значение») и комментариями с описанием.  
  
 Пример файла ConfigurationFile.ini:  
  
```  
; Microsoft SQL Server Configuration file  
[OPTIONS]  
; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE.   
; This is a required parameter.   
ACTION="Install"  
; Specifies features to install, uninstall, or upgrade.   
; The list of top-level features include SQL, AS, RS, IS, and Tools.   
; The SQL feature will install the database engine, replication, and full-text.   
; The Tools feature will install Management Tools, Books online,   
; SQL Server Data Tools, and other shared components.   
FEATURES=SQL,Tools  
```  
  
#### <a name="how-to-generate-a-configuration-file"></a>Создание файла конфигурации  
  
1.  Вставьте установочный носитель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В корневой папке дважды щелкните файл Setup.exe. Чтобы выполнить установку из общей сетевой папки, перейдите в корневую папку общего ресурса и дважды щелкните файл setup.exe.  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Edition не создает файл конфигурации автоматически. Следующая команда запустит установку и создаст файл конфигурации.  
    >   
    >  SETUP.exe /UIMODE=Normal /ACTION=INSTALL  
  
2.  Следуйте указаниям мастера до страницы **Все готово для установки** . Путь к файлу конфигурации указывается на странице **Все готово для установки** в разделе пути файла конфигурации. Дополнительные сведения об установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Установка SQL Server 2014 с помощью мастера установки &#40;установки&#41;](install-sql-server-from-the-installation-wizard-setup.md).  
  
3.  Отмените установку, не завершая ее, чтобы создать INI-файл.  
  
    > [!NOTE]  
    >  Инфраструктура программы установки запишет все соответствующие параметры для запущенных действий (за исключением конфиденциальных данных, например паролей). Параметр /IAcceptSQLServerLicenseTerms также не записывается в файл конфигурации и требует или изменения файла конфигурации, или указания значения в командной строке. Дополнительные сведения см. в статье [Установка SQL Server 2014 из командной строки](install-sql-server-from-the-command-prompt.md). Также включается значение для логических параметров, для которых значения обычно не указываются через командную строку.  
  
## <a name="using-the-configuration-file-to-install-includessnoversionincludesssnoversion-mdmd"></a>Использование файла конфигурации для установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Файл конфигурации можно использовать только при установке из командной строки.  
  
> [!NOTE]  
>  Если необходимо изменить файл конфигурации, рекомендуется создать копию и работать с ней.  
  
#### <a name="how-to-use-a-configuration-file-to-install-a-stand-alone-includessnoversionincludesssnoversion-mdmd-instance"></a>Использование файла конфигурации для установки изолированного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Запустите установку через командную строку и предоставьте файл ConfigurationFile.ini с помощью параметра *ConfigurationFile* .  
  
#### <a name="how-to-use-a-configuration-file-to-prepare-and-complete-an-image-of-a-stand-alone-includessnoversionincludesssnoversion-mdmd-instance-sysprep"></a>Использование файла конфигурации для подготовки и завершения создания образа изолированного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SysPrep)  
  
1.  Подготовка одного или нескольких экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и настройка их на одном и том же компьютере.  
  
    -   Запустите **Подготовка образа изолированного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** на странице **Дополнительно** центра установки и сохраните файл конфигурации подготовки образа.  
  
    -   Используйте тот же файл конфигурации подготовки образа как шаблон для подготовки дополнительных экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Запустите **Завершение образа подготовленного изолированного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** со страницы **Дополнительно** центра установки для настройки подготовленных экземпляров на этом компьютере.  
  
2.  Подготовка образа операционной системы, включая ненастроенный подготовленный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с помощью средства Windows SysPrep.  
  
    -   Запустите **Подготовка образа изолированного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** со страницы "Дополнительно" центра установки и сохраните файл конфигурации подготовки образа.  
  
    -   Запустите **Завершение образа подготовленного изолированного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** со страницы **Дополнительно** центра установки, но отмените процесс на странице **Все готово к завершению образа** после сохранения готового файла конфигурации.  
  
    -   Готовый файл конфигурации можно сохранить в образе Windows для автоматизации настройки подготовленных экземпляров.  
  
#### <a name="how-to-install-a-includessnoversionincludesssnoversion-mdmd-failover-cluster-using-the-configuration-file"></a>Установка отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью файла конфигурации  
  
1.  Вариант интегрированной установки (создайте на узле отказоустойчивого кластера из одного узла, а для добавления дополнительных узлов выполните на них операцию AddNode):  
  
    -   Выберите параметр «Установить отказоустойчивый кластер» и сохраните файл конфигурации, в котором перечисляются все параметры установки.  
  
    -   Запустите установку отказоустойчивого кластера из командной строки, указав параметр *ConfigurationFile* .  
  
    -   На дополнительном добавляемом узле следует запустить действие добавления узла, чтобы сохранить файл ConfigurationFile.ini, применяемый к существующему отказоустойчивому кластеру.  
  
    -   Запустите действие добавления узла через командную строку на всех дополнительных узлах, которые будут присоединены к отказоустойчивому кластеру, предоставив тот же файл конфигурации с помощью параметра ConfigurationFile.  
  
2.  Параметр расширенной установки (подготовка отказоустойчивого кластера на всех узлах отказоустойчивого кластера, затем после подготовки всех узлов — завершение создания кластера на узле, которому принадлежит общий диск).  
  
    -   Запустите действие **Подготовка** на одном из узлов и сохраните файл ConfigurationFile.ini.  
  
    -   Предоставьте тот же файл ConfigurationFile.ini на всех узлах, которые будут подготовлены для отказоустойчивого кластера.  
  
    -   После подготовки всех узлов выполните операцию завершения создания отказоустойчивого кластера на узле, которому принадлежит общий диск, и сохраните файл ConfigurationFile.ini.  
  
    -   После этого можно предоставить данный файл ConfigurationFile.ini, чтобы завершить создание отказоустойчивого кластера.  
  
#### <a name="how-to-add-or-remove-a-node-to-a-includessnoversionincludesssnoversion-mdmd-failover-cluster-using-the-configuration-file"></a>Добавление или удаление узла из отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием файла конфигурации  
  
-   Если существует файл конфигурации, который ранее использовался для добавления или удаления узла из отказоустойчивого кластера, его можно повторно использовать для добавления или удаления дополнительных узлов.  
  
#### <a name="how-to-upgrade-a-includessnoversionincludesssnoversion-mdmd-failover-cluster-using-the-configuration-file"></a>Обновление отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием файла конфигурации  
  
1.  Выполните обновление на пассивном узле и сохраните файл ConfigurationFile.ini. Это можно сделать, не только выполнив реальное обновление, но и отменив его в конце (не выполняя реальное обновление).  
  
2.  Файл ConfigurationFile.ini необходимо предоставить на дополнительных обновляемых узлах, чтобы завершить процесс.  
  
## <a name="sample-syntax"></a>Образец синтаксиса  
 Ниже приведено несколько примеров использования файла конфигурации.  
  
-   Указание файла конфигурации в командной строке:  
  
```  
Setup.exe /ConfigurationFile=MyConfigurationFile.INI  
```  
  
-   Указание паролей в командной строке, а не в файле конфигурации:  
  
```  
Setup.exe /SQLSVCPASSWORD="************" /AGTSVCPASSWORD="************" /ASSVCPASSWORD="************" /ISSVCPASSWORD="************" /RSSVCPASSWORD="************" /ConfigurationFile=MyConfigurationFile.INI  
```  
  
## <a name="see-also"></a>См. также  
 [Установка SQL Server 2014 из командной строки](install-sql-server-from-the-command-prompt.md)   
 [Установка отказоустойчивого кластера SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)   
 [Обновление отказоустойчивого кластера SQL Server](../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance.md)  
  
  
