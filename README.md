# covid-solver-queue
## api handlers
- GET /counter 
  Returns current package number that should be calculated. First we empty the leftover list (filled every two hours with lookup to the ftp server), after all of those are taken, we continue on incrementing active counter.
  
- GET /file/down/:counter 
  Returns actual package with number passed as argument (/file/down/16)

- GET /file/target/test_pro
  Returns TARGETS/TEST_PRO.pdb which is downloaded from ftp only once and after that we use cached version.
  
- GET /file/target/test_ref
  Returns TARGETS/TEST_REF.sdf which is downloaded from ftp only once and after that we use cached version.
  
- POST /file/:counter
  Uploads calcualted file to the ftp server. (upload with curl -F "data=@OUT_16.sdf" http://server.domain.com/file/16 )
  
- GET /current
  Returns current active counter
  
- GET /leftovers
  Returns leftovers
  
- GET /health
  Returns "ok" if server is alive and kicking