postgresinit:
	docker run --name postgres16 -p 5432:5432 -e POSTGRES_USER=root -e POSTGRES_PASSWORD=secret -d postgres:16-alpine

postgres:
	docker exec -it postgres16 psql

creaatedb:
	docker exec -it postgres16 createdb --username=root --owner=root go-chat

dropdb:
	docker exec -it postgres16 dropdb go-chat

migrateup:
	 migrate -path db/migrations -database "postgresql://root:secret@localhost:5432/go-chat?sslmode=disable" -verbose up

migratedown:
	 migrate -path db/migrations -database "postgresql://root:secret@localhost:5432/go-chat?sslmode=disable" -verbose down


.PHONY: postgresinit, postgres, creaatedb, dropdb, migrateup,migratedown