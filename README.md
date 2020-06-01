# oracle-plsql-email-format-validate
oracle-plsql-email-format-validate

### Email Validation Check

```
REGEXP_LIKE (EMAIL, '^[A-Za-z]+[A-Za-z0-9.]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}$');
```

The email validation on the list of emails can be performed to check whether any of them violate the rules of email ID creation.

The below query statement selects the email IDs with the below rules:

1. The starting character must be an alphabet which is handled by the condition ```^[A-Za-z0-9.]```

2. The first part of the mail ID must contain only alphabets, numbers and periods which is handled by the condition ```[A-Za-z0-9.]```

3. The second part of the mail ID must be prefixed with an <b>at the rate of</b> (@) symbol and may contain only alphabets, numbers, hyphens and periods in them. This is handled by the condition ```@[A-Za-z0-9.-]```.

4. The last and third part of the mail ID must be prefixed with a DOT followed by alphabets not less than two and no more than four. This is handled by the condition ```\.[A-Za-z]{2,4}$```. Here, ```\.``` searches for the literal character DOT


Sample:
```
WITH t AS
  (SELECT 'brucewayne.1981@gmail.com' email FROM dual
  UNION ALL
  SELECT 'clark_kent@gmail.com' FROM dual
  UNION ALL
  SELECT '1Tonystark.1980@gmail.com' FROM dual
  UNION ALL
  SELECT 'peter@parker.1989@gmail.com' FROM dual
  )
SELECT *
FROM t
WHERE REGEXP_LIKE (EMAIL, '^[A-Za-z]+[A-Za-z0-9.]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}$');
```

Result:
```
brucewayne.1981@gmail.com
```

Source: [from this](http://www.dba-oracle.com/t_email_validation_regular_expressions.htm).
