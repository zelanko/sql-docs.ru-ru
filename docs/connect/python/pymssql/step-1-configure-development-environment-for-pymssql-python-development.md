---
title: 'Шаг 1: Настройка среды разработки Python pymssql | Документы Microsoft'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6d392a5e-b08e-4b35-9e99-61260888fc41
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6a4a573ce609bfb5364a1dabac784eb760915b8a
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35309523"
---
# <a name="step-1-configure-development-environment-for-pymssql-python-development"></a>Шаг 1: Настройка среды разработки для pymssql разработки Python
Необходимо будет настроить среду разработки с необходимых компонентов для разработки приложений с помощью драйвера Python для SQL Server.    
  
Обратите внимание, что драйверы SQL Python использовать протокол потока табличных данных, который включен по умолчанию в SQL Server и базы данных SQL Azure.  Дополнительная настройка не требуется.  
  
## <a name="windows"></a>Windows  
  
1. **Установка среды выполнения Python и pip диспетчера пакетов**  
A. Последовательно выберите пункты [python.org](https://www.python.org/downloads/)  
Б. Щелкните соответствующую ссылку MSI-файл установщика Windows.   
в. Один раз загруженный выполнения MSI-файл для установки среды выполнения Python  
  
2. **Загрузка модуля pymssql** из [здесь](http://www.lfd.uci.edu/~gohlke/pythonlibs/#pymssql)  
  
    Убедитесь, что выбран правильный whl файл.  Например: Если вы используете Python 2.7 на 64-разрядном компьютере выберите: pymssql‑2.1.1‑cp27‑none‑win_amd64.whl. После загрузки файла .whl поместите его в папке C:/Python27.  
      
3. **Откройте cmd.exe**  
  
4. **Установка модуля pymssql**     
    Например, при использовании Python 2.7 на 64-разрядном компьютере:  
```  
> cd c:\Python27  
> pip install pymssql‑2.1.1‑cp27‑none‑win_amd64.whl  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Установка среды выполнения Python и pip диспетчера пакетов** Python предварительно предустановлено на большинством дистрибутивов Ubuntu.  Если компьютер не имеет установки python, можно получить либо загрузки архива tar источника из [python.org](https://www.python.org/downloads/) создать локально, или можно использовать диспетчер пакетов:  
```  
> sudo apt-get install python   
```  
  
2.  **Откройте терминалов**  
  
3.  **Установите модуль pymssql и зависимости**  
```  
> sudo apt-get --assume-yes update  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
> sudo apt-get --assume-yes install python-dev python-pip  
> sudo pip install pymssql  
```  
  
## <a name="mac"></a>Mac  
  
1. **Установка среды выполнения Python и pip диспетчера пакетов**  
A. Последовательно выберите пункты [python.org](https://www.python.org/downloads/)  
Б. Щелкните соответствующую ссылку pkg Mac установщика.   
в. Один раз загруженный выполнения pkg для установки среды выполнения Python  
  
2.  **Откройте терминалов**  
  
3. **Установка диспетчера пакетов Homebrew**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
4.  **Установка модуля FreeTDS**  
```  
> brew install FreeTDS  
```  
  
5.  **Установка модуля pymssql**  
```  
> sudo -H pip install pymssql  
```
