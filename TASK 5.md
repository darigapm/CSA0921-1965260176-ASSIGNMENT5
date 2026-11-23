# Task 5 – Design for Correctness and Safety

## Atomic Transactions & SQL Injection Prevention
```text
ALGORITHM TransferMoney (con, fromWallet, toWallet, amount)
1. SET autoCommit <- false
2. TRY
3.     UPDATE wallet SET balance = balance - amount WHERE id = fromWallet
4.     UPDATE wallet SET balance = balance + amount WHERE id = toWallet
5.     COMMIT
6. CATCH any error
7.     ROLLBACK
8. FINALLY
9.     RESTORE autoCommit
END
