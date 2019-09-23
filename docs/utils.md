# Utils

!!! note "Links"
    * [Admin LTE](https://www.npmjs.com/package/angular-admin-lte)
    * [Materials](https://material.io/)
    * [MKDocs Material docs](https://squidfunk.github.io/mkdocs-material/getting-started/
 ---

# PostgreSQL 

```SQL
DO
$$

DECLARE
   r1   record;

BEGIN
   IF NOT EXISTS(SELECT ...) 
   THEN
      CREATE TRIGGER ...
   END IF;

   FOR r1 IN (SELECT ...)
   LOOP
      INSERT INTO ...
   END LOOP;

   BEGIN
      CREATE INDEX tabela_idx_campo ON public.tabela
       USING btree (campo);
   EXCEPTION
      -- Para descobrir o tipo da exceção com base no valor da variével "SQLSTATE" use o link:
      -- https://www.postgresql.org/docs/devel/static/errcodes-appendix.html
      WHEN duplicate_table THEN
         RAISE NOTICE '%', SQLERRM;
      WHEN others THEN
         RAISE EXCEPTION '% %', SQLERRM, SQLSTATE;
   END;
END;
$$;
```
