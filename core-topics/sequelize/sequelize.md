# Sequelize Notes

## Models

- a model is a usable representation of data and will typically match up to the tables in our SQL database.
- Blueprints of models are called schemas. We are going to use Sequelize's `define` method to define what our data should look like (and by extension, how Sequelize should construct its models of that data).

# `.sync`

Sequelize models have a synchronization functionality built in. Check out the [documentation on the Model.sync method](http://docs.sequelizejs.com/manual/tutorial/models-definition.html#database-synchronization). This method allows us to take each of our models (Page and User), call .sync on each and Sequelize will run queries against our database to create the needed tables and columns if they don't exist.

Where to place? An appropriate place might be before your server is calling its .listen method with a port. This prevents us from running into a race condition where users are able to make requests to the database before it is synced.

Keep in mind that

- sync is an asynchronous operation (it is interacting with the database) and returns a promise.
- Because it returns a promise, it needs to be within an async function if you want to use await.
- this is for dev environments only; in production we will not be resetting our database frequently.

## Relation or Associations

- This will establish a connection that describes that a page has one user associated with it and that information will be established on the pages table rows (as opposed to on users rows). It should be placed in your models/index.js. The pages table (check your GUI) should have a new column authorId which will contain the id of the user associated with this page.
  `Page.belongsTo(User, { as: 'author' });`

# [Detailed Sequelize Study Guide](https://learn.fullstackacademy.com/workshop/5a68bdb4d749e900042aa7ee/content/5a68bdb4d749e900042aa83a/text)

The following is a more in-depth review outline covering most everything that we expect you to become familiar with. Keep in mind that this doesn't mean you should *memorize* everything --- rather, seek to *understand concepts* and be comfortable *looking up in the docs*.

- ORMs in general
  - There are challenges in marrying SQL tables to JS variables (e.g. Objects)
  - The Object-Relational Impedance Mismatch (general concept, no specifics)
  - An ORM enables programmatic access to SQL tables / rows, *modeling* relational data as *objects* with properties and methods.
- What are the roles of our tools?
  - **Postgres** (an RDBMS process) which accepts incoming SQL via TCP/IP and does disk operations
  - `pg` (the Node-Postgres driver) lets our Node JS apps communicate via TCP/IP to Postgres
  - **Sequelize** (an ORM using `pg`) abstracts away SQL queries by giving us objects with properties and methods
- Sequelize
  - [Initialization](https://sequelize-guides.netlify.com/getting-started/)
    - Installation: `npm install --save sequelize`
    - Installation of required dependencies for Postgres: `npm install --save pg@6 pg-hstore`
    - How to create a `db` connection instance with `new Sequelize` + a Postgres connection string
    - Use `{logging: false}` to disable SQL query logging if you prefer
  - [Creating models](https://sequelize-guides.netlify.com/model-definition/)
    - What a Sequelize model is / does / represents
    - How to use a Sequelize `db` instance to define a model
      - Setting up schema fields (aka attributes)
        - Specifying [types](https://sequelize-guides.netlify.com/column-types/), e.g.
          - `Sequelize.STRING`
          - `Sequelize.TEXT`
          - `Sequelize.ENUM('val1', 'val2')` ...and many others
        - Specifying [validations](https://sequelize-guides.netlify.com/validators-and-default-values/), e.g.
          - `allowNull`
          - `isEmail`
          - `notEmpty`
          - `min` ...and many others
        - Specifying a `defaultValue`
      - Registering [hooks](https://sequelize-guides.netlify.com/hooks/), e.g.
        - `beforeValidate`
        - `beforeDestroy` ...and others
    - [Associating models](https://sequelize-guides.netlify.com/association-types/)
      - What associations are and how they relate to actual Joins (SQL)
      - Basic conceptual results of defining an association between models
        - Tables are modified to have foreign keys, or even join tables are constructed
        - "Magic" class and instance methods, e.g. `someFoo.getBar()`, are created
      - Some familiarity with different association schemes and how Sequelize accomplishes them, e.g.
        - `belongsTo`
        - `hasOne`
        - `hasMany`
        - `belongsToMany`
        - ...and others
    - [Synchronizing models](http://docs.sequelizejs.com/manual/tutorial/models-definition.html#database-synchronization)
      - What synchronization is --- how Sequelize uses model definitions to create (or update) SQL tables
      - using `SomeModel.sync()` with multiple models
      - alternatively, using `db.sync()` to sync all models
      - what `{force: true}` does, and how it is different from default behavior
  - Using models and instances
    - Exporting models & requiring them in your router files
    - [Querying in general](https://sequelize-guides.netlify.com/querying/), including:
      - [Search operators](https://sequelize-guides.netlify.com/search-operators/), e.g. `$ne` and `$in`, for richer filtering
    - Standard model & instance methods for [Inserting, updating and destroying](https://sequelize-guides.netlify.com/inserting-updating-destroying/)

## Associations cheat sheet

### One To One **\*\***\*\***\*\***\*\***\*\***\*\***\*\***\*\*\*\***\*\***\*\***\*\***\*\***\*\***\*\***\*\***

1. belongTo <- BelongsTo associations are associations where the foreign key for the one-to-one relation exists on the source model.

<source> <target>

Food.belongsTo(Puppy) // - going to add puppyId to the food table (source model), to hold the primary key value for Puppy

By default the foreign key for a belongsTo relation will be generated from the target model name and the target primary key name.

In cases where "as" has been defined it will be used in place of the target model name.

Food.belongsTo(Puppy, {foreignKey: 'big_pups'}) // <=big_pups pls note an absence of Id

Food.belongsTo(Puppy, {as: 'very_big_pups'}) // <=veryBigPupsId pls note a camel case

2. HasOne

HasOne associations are associations where the foreign key for the one-to-one relation exists on the target model.

Puppy.hasOne(Food) // - going to add puppyId on the target model (Food table).

Food.hasOne(Puppy) // - going to add foodId on the target model (Puppy table).

Puppy.hasOne(Food, {foreignKey: 'food_lovers'}) // <=food_lovers on the target model (Food table).

Puppy.hasOne(Food, {as: 'one_meal'}) // <=oneMealId

### Difference between HasOne and BelongsTo **\*\***\*\*\*\***\*\***\*\*\***\*\***\*\*\*\***\*\***

They are suitable for different scenarios. When we link two model in Sequelize we can refer them as pairs of source and target models.

HasOne and BelongsTo insert the association key in different models from each other.

HasOne inserts the association key in target model whereas BelongsTo inserts the association key in the source model.

### One-To-Many **\*\*\*\***\*\*\*\***\*\*\*\***\***\*\*\*\***\*\*\*\***\*\*\*\***

One-To-Many associations are connecting one source with multiple targets. The targets however are again

connected to exactly one specific source.

Puppy.hasMany(Food, {as: 'Meals'}) // - going to add puppyId on the target model (Food table)

Instances of Puupy will get the accessors getMeals and setMeals. We could just leave it the way

it is and let it be a one-way association. But we want more! Let's define it the other way around by

creating a many to many association in the next section:

### Belongs-To-Many **\*\*\*\***\*\*\*\*******\*\*\*\*******

Belongs-To-Many associations are used to connect sources with multiple targets.

Furthermore the targets can also have connections to multiple sources.

Puppy.belongsToMany(Food, {through: 'puppiesFoods' })

Food.belongsToMany(Puppy, {through: 'puppiesFoods' })

This will create a new model called puppiesFoods with the equivalent foreign keys foodId and puppyId.

This will add methods getFoods, setFoods, addFoods, addFoods to Puppy, and getPuppy, setPuppy,

addPuppy, and addPuppy to Food.
