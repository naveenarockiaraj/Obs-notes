./orchdown; ./orchrm; ./orchup;
   23  direnv allow
   24  ./orchdown; ./orchrm; ./orchup;
   25  code .
   26  fig kill apisix-init; fig rm -f apisix-init; fig up -d apisix-init;
   27  fig kill apisix; fig rm -f apisix; fig up -d apisix;
   28  fig kill apisix-init; fig rm -f apisix-init; fig up -d apisix-init;
   29  fig kill apisix; fig rm -f apisix; fig up -d apisix;
   30  fig kill ui; fig rm -f ui; fig up -d ui;
   31  fig kill ui; fig rm -f ui; fig up -d ui;
   32  ./orchdown; ./orchrm; ./orchup;
   33  ./orchdown; ./orchrm; ./orchup;
   34  fig kill tlc; fig rm -f tlc; fig up -d tlc;
   35  direnv allow
   36  fig kill tlc; fig rm -f tlc; fig up -d tlc;
   37  ./orchdown; ./orchrm;
   38  ./orchdown; ./orchrm; ./orchup;
   39  ./orchdown; ./orchrm; ./orchup;
   40  fig kill tlc; fig rm -f tlc; fig up -d tlc;
   41  git pull
   42  fig kill tlc; fig rm -f tlc; fig up -d tlc;
   43  direnv allow
   44  fig kill tlc; fig rm -f tlc; fig up -d tlc;
   45  fig kill tlc; fig rm -f tlc; fig up -d tlc;
   46  fig kill tlc; fig rm -f tlc; fig up -d tlc;
   47  fig kill ui; fig rm -f ui; fig up -d ui
   48  fig kill tlc; fig rm -f tlc; fig up -d tlc;
   49  fig kill tlc; fig rm -f tlc; fig up -d tlc;
   50  fig kill tlc; fig rm -f tlc; fig up -d tlc;
   51  ./orchdown; ./orchrm; ./orchup;
   52  fig kill tlc; fig rm -f tlc; fig up -d tlc;
   53  direnv allow
   54  ./orchdown; ./orchrm; ./orchup;
   55  fig exec -it tlc printenv | grep -i S3SC
   56  direnv allow
   57  fig logs -f tlc
   58  git status
   59  git diff .env
   60  fig logs -f tlc
   61  fig logs tlc > tlc.log
   62  vi tlc.log
   63  history