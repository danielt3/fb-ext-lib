ifeq ($(MT), 1)
	DLIB := libext-database.mt.a
	DOBJ := database.mt.o
	DS3O := sqlite3.mt.o
	DS3L := libext-database-driver-sqlite3.mt.a
	DSMYO := mysql.mt.o
	DSMYL := libext-database-driver-mysql.mt.a
	DSPGO := postgre.mt.o
	DSPGL := libext-database-driver-postgre.mt.a
	DXMLO := xml.mt.o
	DXMLL := libext-database-driver-xml.mt.a
else
	DLIB := libext-database.a
	DOBJ := database.o
	DS3O := sqlite3.o
	DS3L := libext-database-driver-sqlite3.a
	DSMYO := mysql.o
	DSMYL := libext-database-driver-mysql.a
	DSPGO := postgre.o
	DSPGL := libext-database-driver-postgre.a
	DXMLO := xml.o
	DXMLL := libext-database-driver-xml.a
endif

build-database : ../../../lib/$(TARGET)/$(DLIB) ../../../lib/$(TARGET)/$(DS3L) ../../../lib/$(TARGET)/$(DSMYL) ../../../lib/$(TARGET)/$(DSPGL) ../../../lib/$(TARGET)/$(DXMLL)

../../../lib/$(TARGET)/$(DLIB) : $(DOBJ)
	$(FBC) $(FBC_LFLAGS) -i ../../../include/freebasic $(DOBJ) -x ../../../lib/$(TARGET)/$(DLIB)

$(DOBJ) : database.bas ../../../include/freebasic/ext/database/database.bi ../../../include/freebasic/ext/database/driver.bi
	$(FBC) $(FBC_CFLAGS) $(IF $(MT),-mt) -i ../../../include/freebasic database.bas -o $(DOBJ)

drivers/$(DS3O) : drivers/sqlite3.bas ../../../include/freebasic/ext/database/driver.bi ../../../include/freebasic/ext/database/drivers/sqlite3.bi
	$(FBC) $(FBC_CFLAGS) $(IF $(MT),-mt) -i ../../../include/freebasic drivers/sqlite3.bas -o drivers/$(DS3O)

../../../lib/$(TARGET)/$(DS3L) : drivers/$(DS3O)
	$(FBC) $(FBC_LFLAGS) $(IF $(MT),-mt) -i ../../../include/freebasic -x ../../../lib/$(TARGET)/$(DS3L) drivers/$(DS3O)

drivers/$(DSMYO) : drivers/mysql.bas ../../../include/freebasic/ext/database/driver.bi ../../../include/freebasic/ext/database/drivers/mysql.bi
	$(FBC) $(FBC_CFLAGS) $(IF $(MT),-mt) -i ../../../include/freebasic drivers/mysql.bas -o drivers/$(DSMYO)

../../../lib/$(TARGET)/$(DSMYL) : drivers/$(DSMYO)
	$(FBC) $(FBC_LFLAGS) $(IF $(MT),-mt) -i ../../../include/freebasic -x ../../../lib/$(TARGET)/$(DSMYL) drivers/$(DSMYO)

drivers/$(DSPGO) : drivers/postgre.bas ../../../include/freebasic/ext/database/driver.bi ../../../include/freebasic/ext/database/drivers/postgre.bi
	$(FBC) $(FBC_CFLAGS) $(IF $(MT),-mt) -i ../../../include/freebasic drivers/postgre.bas -o drivers/$(DSPGO)

../../../lib/$(TARGET)/$(DSPGL) : drivers/$(DSPGO)
	$(FBC) $(FBC_LFLAGS) $(IF $(MT),-mt) -i ../../../include/freebasic -x ../../../lib/$(TARGET)/$(DSPGL) drivers/$(DSPGO)

drivers/$(DXMLO) : drivers/xml.bas ../../../include/freebasic/ext/database/driver.bi ../../../include/freebasic/ext/database/drivers/xml.bi
	$(FBC) $(FBC_CFLAGS) $(IF $(MT),-mt) -i ../../../include/freebasic drivers/xml.bas -o drivers/$(DXMLO)

../../../lib/$(TARGET)/$(DXMLL) : drivers/$(DXMLO)
	$(FBC) $(FBC_LFLAGS) $(IF $(MT),-mt) -i ../../../include/freebasic -x ../../../lib/$(TARGET)/$(DXMLL) drivers/$(DXMLO)

clean-database :
	$(RM) -f database*.o drivers/*.o
	$(RM) -f ../../../lib/$(TARGET)/libext-database*.a

