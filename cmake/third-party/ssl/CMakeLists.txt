cmake_minimum_required ( VERSION 2.8.5 )
project ( ssl )

if ( MOAI_OPENSSL ) 
 set ( CMAKE_CURRENT_SOURCE_DIR "../../../../3rdparty/openssl-1.0.0d/" )
 
 set ( CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DMOAI_WITH_OPENSSL=1" CACHE INTERNAL "doc string" )
 set ( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -DMOAI_WITH_OPENSSL=1" CACHE INTERNAL "doc string" )

 set ( SSL_INCLUDES 
    "../../3rdparty/openssl-1.0.0d/crypto/"
    "../../3rdparty/openssl-1.0.0d/include/"
    "../../3rdparty/openssl-1.0.0d/crypto/asn1/"
    "../../3rdparty/openssl-1.0.0d/crypto/evp/"
    "../../3rdparty/openssl-1.0.0d/"
    
    if ( BUILD_LINUX )
      "../../3rdparty/openssl-1.0.0d/include-linux"
    endif ( BUILD_LINUX )

  CACHE INTERNAL "doc string" )
 
 set ( SSL_SOURCES 

   ${CMAKE_CURRENT_SOURCE_DIR}ssl/bio_ssl.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/d1_both.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/d1_clnt.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/d1_enc.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/d1_lib.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/d1_meth.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/d1_pkt.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/d1_srvr.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/kssl.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/s23_clnt.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/s23_lib.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/s23_meth.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/s23_pkt.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/s23_srvr.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/s2_clnt.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/s2_enc.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/s2_lib.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/s2_meth.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/s2_pkt.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/s2_srvr.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/s3_both.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/s3_clnt.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/s3_enc.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/s3_lib.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/s3_meth.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/s3_pkt.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/s3_srvr.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/ssl.h
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/ssl_algs.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/ssl_asn1.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/ssl_cert.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/ssl_ciph.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/ssl_err2.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/ssl_err.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/ssl_lib.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/ssl_rsa.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/ssl_sess.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/ssl_stat.c
   #${CMAKE_CURRENT_SOURCE_DIR}ssl/ssl_task.c
   #${CMAKE_CURRENT_SOURCE_DIR}ssl/ssltest.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/ssl_txt.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/t1_clnt.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/t1_enc.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/t1_lib.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/t1_meth.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/t1_reneg.c
   ${CMAKE_CURRENT_SOURCE_DIR}ssl/t1_srvr.c
 
 CACHE INTERNAL "doc string" )
 
 include_directories ( 
   "${SSL_INCLUDES}"
 )
 
 add_library ( ssl STATIC 
   ${SSL_SOURCES}
 )
else ( MOAI_OPENSSL )

 set ( CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DMOAI_WITH_OPENSSL=0" CACHE INTERNAL "doc string" )
 set ( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -DMOAI_WITH_OPENSSL=0" CACHE INTERNAL "doc string" )

endif ( MOAI_OPENSSL )