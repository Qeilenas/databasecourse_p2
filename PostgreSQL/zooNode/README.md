# Project creation

Должен быть установлен node.js

`npm init`

`npm install --save sequelize`

`npm install --save pg pg-hstore`

Добавить в корень проекта .gitignore со стройкой `node_modules`

Добавить файл .env, заполнить его данными как в .env.example

Добавляем `.env` в gitignore

Установить глобально

`npm install -g sequelize-cli`

Или подгружать каждый раз

`npx sequelize [command]`

Инициализировать:

`sequelize init`

Создание БД:

`sequelize db:create`

Создание первой модели:

`sequelize model:generate --name guardians --attributes name:string --underscored`

Создание seed:

`sequelize seed:create --name demo-types`

Поменять структуру созданного файла как пример:

```js
'use strict'

module.exports = {
  up: (queryInterface, Sequelize) => {
    return queryInterface.bulkInsert(
      'types',
      [
        {
          name: 'Членистоногие',
          description:
            'Членистоно́гие (лат. Arthropoda, от др.-греч. ἄρθρον — сустав и πούς, род. п. ποδός — нога) — тип первичноротых животных, включающий насекомых, ракообразных, паукообразных и многоножек. По количеству видов и распространённости может считаться самой процветающей группой живых организмов. К представителям этого типа относится 2/3 всех видов живых существ на Земле.',
          created_at: new Date(),
          updated_at: new Date(),
        },
        {
          name: 'Хордовые',
          description:
            'Хо́рдовые (лат. Chordata) — тип вторичноротых животных, для которых характерно наличие энтодермального осевого скелета в виде хорды, которая у высших форм заменяется позвоночником. По строению и функции нервной системы тип хордовых занимает высшее место среди всех животных. В мире известно более 60 000 видов хордовых.',
          created_at: new Date(),
          updated_at: new Date(),
        },
        {
          name: 'Волосатики',
          description:
            'Волоса́тики[1] (лат. Nematomorpha, от др.-греч. νῆμα, родительный падеж νῆματος — нить, μορφή — форма) — тип беспозвоночных животных, личинки которых ведут паразитоидный образ жизни. В ископаемом виде известны с эоцена.',
          created_at: new Date(),
          updated_at: new Date(),
        },
      ],
      {},
    )
  },

  down: (queryInterface, Sequelize) => {
    return queryInterface.bulkDelete('types', null, {})
    /*
      Add reverting commands here.
      Return a promise to correctly handle asynchronicity.

      Example:
      return queryInterface.bulkDelete('People', null, {});
    */
  },
}
```

Запустить выполнение всех seed:

`sequelize-cli db:seed:all` - если такие данные есть, они создадутся ещё раз

`sequelize-cli db:seed --seed 20191005080329-demo-types` - запустить одну конкретную миграцию
