There is a package for create. organize and run migration scripts on MongoDB database
https://www.npmjs.com/package/migrate-mongo

### Brainstorm:
1. Organize migrations in separate private package
2. Expose bin-scripts to check state, run migrations etc.
3. Add package as dependency to (at least) server
4. Check ran migrations on current db
  1. If all migrations applied to DB - exit
  2. If some migrations needs to be applied to DB - apply and exit
5. Consumer of migrations package should depends on exact version of it
6. All migrations should be immutable, if there is a problem with one of it - make another one which will fix that