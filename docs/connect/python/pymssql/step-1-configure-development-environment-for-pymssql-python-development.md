---
title: 'Шаг 1: Настройка среды разработки Python в pymssql | Документация Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6d392a5e-b08e-4b35-9e99-61260888fc41
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b60c7aa0f53be6d9c9a249c69ace6780a318e6f3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47787452"
---
# <a name="step-1-configure-development-environment-for-pymssql-python-development"></a>Шаг 1. Настройка среды разработки для разработки на Python в pymssql
Необходимо будет настроить среду разработки с предварительными требованиями, чтобы разрабатывать приложения, используя драйвер Python для SQL Server.    
  
Обратите внимание на то, что драйверы SQL Python использовать протокол потока табличных данных, который включен по умолчанию в SQL Server и базы данных SQL Azure.  Дополнительная настройка не требуется.  
  
## <a name="windows"></a>Windows  
  
1. **Установите среду выполнения Python и диспетчер пакетов pip**  
A. Перейдите к [python.org](https://www.python.org/downloads/)  
Б. Щелкните соответствующую ссылку msi установщика Windows.   
в. Один раз Скачанный запуска MSI-файл для установки среды выполнения Python  
  
2. **Загрузка модуля pymssql** из [здесь](http://www.lfd.uci.edu/~gohlke/pythonlibs/#pymssql)  
  
    Убедитесь, что выбран правильный файл whl.  Например: Если вы используете Python 2.7 на 64-разрядном компьютере выберите: pymssql‑2.1.1‑cp27‑none‑win_amd64.whl. После загрузки файла whl разместите его в папку C:/Python27 папки.  
      
3. **Откройте cmd.exe**  
  
4. **Установите модуль pymssql**     
    Например, если вы используете Python 2.7 на 64-разрядном компьютере:  
```  
> cd c:\Python27  
> pip install pymssql‑2.1.1‑cp27‑none‑win_amd64.whl  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Установите среду выполнения Python и диспетчер пакетов pip** Python поставляется предварительно установленным в большинстве дистрибутивов Ubuntu.  Если компьютер не установили python, вы можете получить скачайте tar с источником из [python.org](https://www.python.org/downloads/) и хотите создать локально, или можно использовать диспетчер пакетов:  
```  
> sudo apt-get install python   
```  
  
2.  **Открыть терминал**  
  
3.  **Установите pymssql модуля и зависимости**  
```  
> sudo apt-get --assume-yes update  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
> sudo apt-get --assume-yes install python-dev python-pip  
> sudo pip install pymssql  
```  
  
## <a name="mac"></a>Mac  
  
1. **Установите среду выполнения Python и диспетчер пакетов pip**  
A. Перейдите к [python.org](https://www.python.org/downloads/)  
Б. Щелкните соответствующую ссылку pkg установщика Mac.   
в. Один раз Скачанный выполнения пакета для установки среды выполнения Python  
  
2.  **Открыть терминал**  
  
3. **Установка диспетчера пакетов Homebrew**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
4.  **Установка FreeTDS модуля**  
```  
> brew install FreeTDS  
```  
  
5.  **Установите модуль pymssql**  
```  
> sudo -H pip install pymssql  
```
