## Install

### Clone git repository

```
git clone https://github.com/ignat-s/crm-application.git
```

### Install vendors

```
composer install --prefer-dist
```

### Run install command

```
app/console oro:install --env=dev --user-name=admin --user-email=admin@example.com --user-firstname=John --user-lastname=Doe --user-password=admin --sample-data=n --force
```

See detailed information https://github.com/ignat-s/crm-application/tree/master

### Add OroAcme as submodule

```
git submodule add https://github.com/ignat-s/OroAcme.git src/OroAcme
```

## Create virtual host

## Setup PHPStorm

1. Configure PHP (Settings > PHP)
2. Configure tests (Edit configuration > Defaults > PHPUnit)

## Create new bundle

1. Create a directory orocrm-training/src/OroAcme/src/OroAcme/Bundle/TodoListBundle
2. Create bundle class OroAcme\Bundle\TodoListBundle\OroAcmeTodoListBundle
3. Create extension class OroAcme\Bundle\TodoListBundle\DependencyInjection\OroAcmeTodoListExtension

## Register bundle

Create orocrm-training/src/OroAcme/src/OroAcme/Bundle/TodoListBundle/Resources/config/oro/bundles.yml

```
bundles:
    - OroAcme\Bundle\TodoListBundle\OroAcmeTodoListBundle
```

Update cache:

```
app/console cache:clear
```

## Create entities

1. Create TodoItem entity (id, text, status, owner, created at, updated at)
2. Create TodoStatus entity (name, label)
3. Create data fixture for statuses (open, closed, in progress)
4. Update database schema

```
app/console doctrine:schema:update --dump-sql
app/console doctrine:schema:update --force
```

5. Load fixtures of statuses

```
app/console doctrine:fixture:load --fixtures src/OroAcme/src/OroAcme/Bundle/TodoListBundle/DataFixtures/ --append
```