program XOX;
uses crt;
var
  m, oc: array [1..3, 1..3] of integer;
  new1, new2, kol, res, igr: integer;
  
procedure proverka;
var i: integer;
begin
  writeln;
  for i:=1 to 3 do
    begin
      if (m[i,1]=2) and(m[i,2]=2) and (m[i,3]=2) then
        begin
          writeln ('Поздравляем');
          halt (0);
        end;
      if (m[i,1]=1) and(m[i,2]=1) and (m[i,3]=1) then
        begin
          writeln ('Вы проиграли');
          halt (0);
        end;
      if (m[1,i]=2) and(m[2,i]=2) and (m[3,i]=2) then
        begin
          writeln ('Поздравляем');
          halt (0);
        end;
      if (m[1,i]=1) and(m[2,i]=1) and (m[3,i]=1) then
        begin
          writeln ('Вы проиграли');
          halt (0);
        end;
    end;
      if (m[1,1]=2) and(m[2,2]=2) and (m[3,3]=2) then
        begin
          writeln ('Поздравляем');
          halt (0);
        end;
      if (m[1,3]=2) and(m[2,2]=2) and (m[3,1]=2) then
        begin
          writeln ('Поздравляем');
          halt (0);
        end;
      if (m[1,1]=1) and(m[2,2]=1) and (m[3,3]=1) then
        begin
          writeln ('Вы проиграли');
          halt (0);
        end;
      if (m[1,3]=1) and (m[2,2]=1) and (m[3,1]=1) then
        begin
          writeln ('Вы проиграли');
          halt (0);
        end;
end;

procedure vyvod;
  var i,j: integer;
  begin
    ClrScr;
    writeln ('Вы        - Х');
    writeln ('Компьютер - O');
    writeln;
    writeln ('   1 2 3');
    for i:=1 to 3 do
      begin
        write (i,'  ');
        for j:=1 to 3 do
          begin
            if m[i,j]=0 then write ('- ');
            if m[i,j]=1 then write ('O ');
            if m[i,j]=2 then write ('X ');
          end;
        writeln;
      end;
  end;
  
  
procedure WaR;
  var i,j: integer;
  begin
    ClrScr;
    writeln ('Вы        - Х');
    writeln ('Компьютер - O');
    writeln;
    writeln ('   1 2 3');
    for i:=1 to 3 do
      begin
        write (i,'  ');
        for j:=1 to 3 do
          begin
            if m[i,j]=0 then write ('- ');
            if m[i,j]=1 then write ('O ');
            if m[i,j]=2 then write ('X ');
          end;
        writeln;
      end;
    inc (kol);
    proverka;
    if kol<10 then
      begin
        repeat
          write ('Сделайте следующий ход:');
          readln (new1, new2);
        until (new1<=3) and (new1>=1) and (new2<=3) and (new2>=1) and (m[new1,new2]=0);
        m[new1,new2]:=2;
        oc[new1,new2]:=-1;
        proverka;
        inc (kol);
      end
    else
      begin
        write ('Ничья');
        readln;
        halt (0);
      end;
end;




begin
writeln ('Будем играть честно?');
writeln ('1. Да');
writeln ('2. Нет');
read (res);
ClrScr;
if res=1 then begin
  WaR;
  if (m[2,2]=2) then 
    begin
      m[3,3]:=1;
      WaR;
      if (m[3,2]=2) then 
        begin
          m[1,2]:=1;
          WaR;
          if m[1,1]=2 then 
            begin
              m[1,3]:=1;
              WaR;
              if (m[2,1]=2) or (m[3,1]=2) then begin m[2,3]:=1; vyvod; proverka; end;
              if (m[2,3]=2) then begin m[2,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
          if m[2,1]=2 then 
            begin
              m[2,3]:=1;
              WaR;
              if (m[1,1]=2) or (m[3,1]=2) then begin m[1,3]:=1; vyvod; proverka; end;
              if (m[3,1]=2) then begin m[3,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
          if m[3,1]=2 then 
            begin
              m[1,3]:=1;
              WaR;
              if (m[1,1]=2) or (m[2,1]=2) then begin m[2,3]:=1; vyvod; proverka; end;
              if (m[2,3]=2) then begin m[1,1]:=1; vyvod; proverka; end;
            end;
          if m[1,3]=2 then
            begin
              m[3,1]:=1;
              WaR;
              if m[1,1]=2 then begin m[2,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
              if m[2,1]=2 then begin m[2,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
              if m[2,3]=2 then begin m[2,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
          if m[2,3]=2 then 
            begin
              m[2,1]:=1;
              WaR;
              if m[1,1]=2 then begin m[3,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
              if m[3,1]=2 then begin m[1,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
              if m[1,3]=2 then begin m[3,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[2,3]=2) then 
        begin
          m[2,1]:=1;
          WaR;
          if m[1,1]=2 then 
            begin
              m[3,1]:=1;
              WaR;
              if (m[1,2]=2) or (m[1,3]=2) then begin m[3,2]:=1; vyvod; proverka; end;
              if (m[3,2]=2) then begin m[1,2]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
          if m[1,2]=2 then 
            begin
              m[3,2]:=1;
              WaR;
              if (m[1,1]=2) or (m[1,3]=2) then begin m[3,1]:=1; vyvod; proverka; end;
              if (m[3,1]=2) then begin m[1,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
          if m[1,3]=2 then 
            begin
              m[3,1]:=1;
              WaR;
              if (m[1,1]=2) or (m[1,2]=2) then begin m[3,2]:=1; vyvod; proverka; end;
              if (m[3,2]=2) then begin m[1,1]:=1; vyvod; proverka; end;
            end;
          if m[3,1]=2 then 
            begin
              m[1,3]:=1;
              WaR;
              if m[1,1]=2 then begin m[1,2]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
              if m[1,2]=2 then begin m[3,2]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
              if m[3,2]=2 then begin m[1,2]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
          if m[3,2]=2 then 
            begin
              m[1,2]:=1;
              WaR;
              if m[1,1]=2 then begin m[1,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
              if m[1,3]=2 then begin m[3,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
              if m[3,1]=2 then begin m[1,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[3,1]=2) then 
        begin
          m[1,3]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,2]=2) or (m[2,1]=2) or (m[3,2]=2) then begin m[2,3]:=1; vyvod; proverka; end;
          if (m[2,3]=2) then 
            begin
              m[2,1]:=1;
              WaR;
              if m[1,1]=2 then begin m[1,2]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
              if m[1,2]=2 then begin m[3,2]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
              if m[3,2]=2 then begin m[1,2]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[1,3]=2) then 
        begin
          m[3,1]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,2]=2) or (m[2,1]=2) or (m[2,3]=2) then begin m[3,2]:=1; vyvod; proverka; end;
          if (m[3,2]=2) then 
            begin
              m[1,2]:=1;
              WaR;
              if m[1,1]=2 then begin m[2,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
              if m[2,1]=2 then begin m[2,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
              if m[2,3]=2 then begin m[2,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[2,1]=2) then 
        begin
          m[2,3]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,2]=2) or (m[3,1]=2) or (m[3,2]=2) then begin m[1,3]:=1; vyvod; proverka; end;
          if (m[1,3]=2) then 
            begin
              m[3,1]:=1;
              WaR;
              if (m[1,1]=2) or (m[1,2]=2) then begin m[3,2]:=1; vyvod; proverka; end;
              if (m[3,2]=2) then begin m[1,2]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[1,2]=2) then 
        begin
          m[3,2]:=1;
          WaR;
          if (m[1,1]=2) or (m[2,1]=2) or (m[1,3]=2) or (m[2,3]=2) then begin m[3,1]:=1; vyvod; proverka; end;
          if (m[3,1]=2) then 
            begin
              m[1,3]:=1;
              WaR;
              if (m[1,1]=2) or (m[2,1]=2) then begin m[2,3]:=1; vyvod; proverka; end;
              if (m[2,3]=2) then begin m[2,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[1,1]=2) then 
        begin
          m[3,1]:=1;
          WaR;
          if (m[1,2]=2) or (m[1,3]=2) or (m[2,1]=2) or (m[2,3]=2) then begin m[3,2]:=1; vyvod; proverka; end;
          if (m[3,2]=2) then 
            begin
              m[1,2]:=1;
              WaR;
              if m[1,3]=2 then begin m[2,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
              if m[2,1]=2 then begin m[2,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
              if m[2,3]=2 then begin m[2,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
    end;
  if (m[3,1]=2) then 
    begin
      m[2,2]:=1;
      WaR;
      if (m[2,1]=2) then 
        begin
          m[2,3]:=1;
          WaR;
          if (m[1,2]=2) or (m[1,3]=2) or (m[2,3]=2) or (m[3,2]=2) then begin m[3,3]:=1; vyvod; proverka; end;
          if (m[3,3]=2) then
            begin
              m[3,2]:=1;
              WaR;
              if (m[1,3]=2) or (m[2,3]=2) then begin m[1,2]:=1; vyvod; proverka; end;
              if (m[1,2]=2) then begin m[1,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[3,2]=2) then 
        begin
          m[3,3]:=1;
          WaR;
          if (m[2,1]=2) or (m[1,2]=2) or (m[1,3]=2) or (m[2,3]=2) then begin m[1,1]:=1; vyvod; proverka; end;
          if (m[1,1]=2) then
            begin
              m[2,1]:=1;
              WaR;
              if (m[1,2]=2) or (m[1,3]=2) then begin m[2,3]:=1; vyvod; proverka; end;
              if (m[2,3]=2) then begin m[1,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[1,1]=2) then 
        begin
          m[2,1]:=1;
          WaR;
          if (m[1,2]=2) or (m[1,3]=2) or (m[3,1]=2) or (m[3,3]=2) then begin m[2,3]:=1; vyvod; proverka; end;
          if (m[2,3]=2) then
            begin
              m[3,2]:=1;
              WaR;
              if (m[1,3]=2) or (m[3,3]=2) then begin m[1,2]:=1; vyvod; proverka; end;
              if (m[1,2]=2) then begin m[1,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[3,3]=2) then 
        begin
          m[3,2]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,3]=2) or (m[2,1]=2) or (m[2,3]=2) then begin m[1,2]:=1; vyvod; proverka; end;
          if (m[1,2]=2) then
            begin
              m[2,1]:=1;
              WaR;
              if (m[1,1]=2) or (m[1,3]=2) then begin m[2,3]:=1; vyvod; proverka; end;
              if (m[2,3]=2) then begin m[1,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[1,2]=2) then 
        begin
          m[2,1]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,3]=2) or (m[3,2]=2) or (m[3,3]=2) then begin m[2,3]:=1; vyvod; proverka; end;
          if (m[2,3]=2) then
            begin
              m[3,3]:=1;
              WaR;
              if (m[1,3]=2) or (m[3,2]=2) then begin m[1,1]:=1; vyvod; proverka; end;
              if (m[1,1]=2) then begin m[1,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[2,3]=2) then 
        begin
          m[3,2]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,3]=2) or (m[2,1]=2) or (m[3,3]=2) then begin m[1,2]:=1; vyvod; proverka; end;
          if (m[1,2]=2) then
            begin
              m[1,1]:=1;
              WaR;
              if (m[2,1]=2) or (m[1,3]=2) then begin m[3,3]:=1; vyvod; proverka; end;
              if (m[3,3]=2) then begin m[1,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[1,3]=2) then 
        begin
          m[3,2]:=1;
          WaR;
          if (m[1,1]=2) or (m[2,1]=2) or (m[2,3]=2) or (m[3,3]=2) then begin m[1,2]:=1; vyvod; proverka; end;
          if (m[1,2]=2) then
            begin
              m[1,1]:=1;
              WaR;
              if (m[2,1]=2) or (m[2,3]=2) then begin m[3,3]:=1; vyvod; proverka; end;
              if (m[3,3]=2) then begin m[2,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
    end;
  if (m[1,1]=2) then 
    begin
      m[2,2]:=1;
      War;
      if (m[1,2]=2) then 
        begin
          m[1,3]:=1;
          WaR;
          if (m[2,1]=2) or (m[2,3]=2) or (m[3,2]=2) or (m[3,3]=2) then begin m[3,1]:=1; vyvod; proverka; end;
          if (m[3,1]=2) then
            begin
              m[2,1]:=1;
              WaR;
              if (m[3,2]=2) or (m[3,3]=2) then begin m[2,3]:=1; vyvod; proverka; end;
              if (m[2,3]=2) then begin m[3,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[1,3]=2) then 
        begin
          m[1,2]:=1;
          WaR;
          if (m[2,1]=2) or (m[3,1]=2) or (m[2,3]=2) or (m[3,3]=2) then begin m[3,2]:=1; vyvod; proverka; end;
          if (m[3,2]=2) then
            begin
              m[2,1]:=1;
              WaR;
              if (m[3,1]=2) or (m[3,3]=2) then begin m[2,3]:=1; vyvod; proverka; end;
              if (m[2,3]=2) then begin m[3,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[2,1]=2) then 
        begin
          m[3,1]:=1;
          WaR;
          if (m[1,2]=2) or (m[2,3]=2) or (m[3,2]=2) or (m[3,3]=2) then begin m[1,3]:=1; vyvod; proverka; end;
          if (m[1,3]=2) then
            begin
              m[1,2]:=1;
              WaR;
              if (m[2,3]=2) or (m[3,3]=2) then begin m[3,2]:=1; vyvod; proverka; end;
              if (m[3,2]=2) then begin m[3,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[2,3]=2) then 
        begin
          m[1,2]:=1;
          WaR;
          if (m[2,1]=2) or (m[3,1]=2) or (m[1,3]=2) or (m[3,3]=2) then begin m[3,2]:=1; vyvod; proverka; end;
          if (m[3,2]=2) then
            begin
              m[3,1]:=1;
              WaR;
              if (m[2,1]=2) or (m[3,3]=2) then begin m[1,3]:=1; vyvod; proverka; end;
              if (m[1,3]=2) then begin m[3,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[3,1]=2) then 
        begin
          m[2,1]:=1;
          WaR;
          if (m[1,2]=2) or (m[1,3]=2) or (m[3,2]=2) or (m[3,3]=2) then begin m[2,3]:=1; vyvod; proverka; end;
          if (m[2,3]=2) then
            begin
              m[1,2]:=1;
              WaR;
              if (m[1,3]=2) or (m[3,3]=2) then begin m[3,2]:=1; vyvod; proverka; end;
              if (m[3,2]=2) then begin m[3,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[3,2]=2) then 
        begin
          m[2,1]:=1;
          WaR;
          if (m[1,2]=2) or (m[1,3]=2) or (m[3,1]=2) or (m[3,3]=2) then begin m[2,3]:=1; vyvod; proverka; end;
          if (m[2,3]=2) then
            begin
              m[1,3]:=1;
              WaR;
              if (m[1,2]=2) or (m[3,3]=2) then begin m[3,1]:=1; vyvod; proverka; end;
              if (m[3,1]=2) then begin m[3,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[3,3]=2) then 
        begin
          m[1,2]:=1;
          WaR;
          if (m[2,1]=2) or (m[3,1]=2) or (m[1,3]=2) or (m[2,3]=2) then begin m[3,2]:=1; vyvod; proverka; end;
          if (m[3,2]=2) then
            begin
              m[3,1]:=1;
              WaR;
              if (m[2,1]=2) or (m[2,3]=2) then begin m[1,3]:=1; vyvod; proverka; end;
              if (m[1,3]=2) then begin m[2,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
    end;
  if (m[1,3]=2) then 
    begin
      m[2,2]:=1;
      WaR;
      if (m[1,1]=2) then 
        begin
          m[1,2]:=1;
          WaR;
          if (m[2,1]=2) or (m[3,1]=2) or (m[2,3]=2) or (m[3,3]=2) then begin m[3,2]:=1; vyvod; proverka; end;
          if (m[3,2]=2) then
            begin
              m[2,1]:=1;
              WaR;
              if (m[3,1]=2) or (m[3,3]=2) then begin m[2,3]:=1; vyvod; proverka; end;
              if (m[2,3]=2) then begin m[3,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[1,2]=2) then 
        begin
          m[1,1]:=1;
          WaR;
          if (m[2,1]=2) or (m[3,1]=2) or (m[3,2]=2) or (m[2,3]=2) then begin m[3,3]:=1; vyvod; proverka; end;
          if (m[3,3]=2) then
            begin
              m[2,3]:=1;
              WaR;
              if (m[3,1]=2) or (m[3,2]=2) then begin m[2,1]:=1; vyvod; proverka; end;
              if (m[2,1]=2) then begin m[3,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[2,1]=2) then 
        begin
          m[1,2]:=1;
          WaR;
          if (m[1,1]=2) or (m[3,1]=2) or (m[2,3]=2) or (m[3,3]=2) then begin m[3,2]:=1; vyvod; proverka; end;
          if (m[3,2]=2) then
            begin
              m[3,3]:=1;
              WaR;
              if (m[3,1]=2) or (m[2,3]=2) then begin m[1,1]:=1; vyvod; proverka; end;
              if (m[1,1]=2) then begin m[3,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[2,3]=2) then 
        begin
          m[3,3]:=1;
          WaR;
          if (m[1,2]=2) or (m[2,1]=2) or (m[3,1]=2) or (m[3,2]=2) then begin m[1,1]:=1; vyvod; proverka; end;
          if (m[1,1]=2) then
            begin
              m[1,2]:=1;
              WaR;
              if (m[2,1]=2) or (m[3,1]=2) then begin m[3,2]:=1; vyvod; proverka; end;
              if (m[3,2]=2) then begin m[3,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[3,1]=2) then 
        begin
          m[1,2]:=1;
          WaR;
          if (m[1,1]=2) or (m[2,1]=2) or (m[2,3]=2) or (m[3,3]=2) then begin m[3,2]:=1; vyvod; proverka; end;
          if (m[3,2]=2) then
            begin
              m[3,3]:=1;
              WaR;
              if (m[2,1]=2) or (m[2,3]=2) then begin m[1,1]:=1; vyvod; proverka; end;
              if (m[1,1]=2) then begin m[2,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[3,2]=2) then 
        begin
          m[2,3]:=1;
          WaR;
          if (m[1,1]=2) or (m[3,1]=2) or (m[1,2]=2) or (m[3,3]=2) then begin m[2,1]:=1; vyvod; proverka; end;
          if (m[2,1]=2) then
            begin
              m[1,1]:=1;
              WaR;
              if (m[1,2]=2) or (m[3,1]=2) then begin m[3,3]:=1; vyvod; proverka; end;
              if (m[3,3]=2) then begin m[3,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[3,3]=2) then 
        begin
          m[2,3]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,2]=2) or (m[3,1]=2) or (m[3,2]=2) then begin m[2,1]:=1; vyvod; proverka; end;
          if (m[2,1]=2) then
            begin
              m[3,2]:=1;
              WaR;
              if (m[1,1]=2) or (m[3,1]=2) then begin m[1,2]:=1; vyvod; proverka; end;
              if (m[1,2]=2) then begin m[1,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
    end;
  if (m[3,3]=2) then 
    begin
      m[2,2]:=1;
      WaR;
      if (m[1,1]=2) then 
        begin
          m[1,2]:=1;
          WaR;
          if (m[1,3]=2) or (m[2,1]=2) or (m[2,3]=2) or (m[3,1]=2) then begin m[3,2]:=1; vyvod; proverka; end;
          if (m[3,2]=2) then
            begin
              m[3,1]:=1;
              WaR;
              if (m[2,1]=2) or (m[2,3]=2) then begin m[1,3]:=1; vyvod; proverka; end;
              if (m[1,3]=2) then begin m[2,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[1,2]=2) then 
        begin
          m[2,3]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,3]=2) or (m[3,1]=2) or (m[3,2]=2) then begin m[2,1]:=1; vyvod; proverka; end;
          if (m[2,1]=2) then
            begin
              m[3,1]:=1;
              WaR;
              if (m[1,1]=2) or (m[3,2]=2) then begin m[1,3]:=1; vyvod; proverka; end;
              if (m[1,3]=2) then begin m[1,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[1,3]=2) then
        begin
          m[2,3]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,2]=2) or (m[3,1]=2) or (m[3,2]=2) then begin m[2,1]:=1; vyvod; proverka; end;
          if (m[2,1]=2) then
            begin
              m[3,2]:=1;
              WaR;
              if (m[1,1]=2) or (m[3,1]=2) then begin m[1,2]:=1; vyvod; proverka; end;
              if (m[1,2]=2) then begin m[1,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[2,1]=2) then 
        begin
          m[3,2]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,3]=2) or (m[3,1]=2) or (m[2,3]=2) then begin m[1,2]:=1; vyvod; proverka; end;
          if (m[1,2]=2) then
            begin
              m[1,3]:=1;
              WaR;
              if (m[1,1]=2) or (m[2,3]=2) then begin m[3,1]:=1; vyvod; proverka; end;
              if (m[3,1]=2) then begin m[1,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[2,3]=2) then 
        begin
          m[1,3]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,2]=2) or (m[3,1]=2) or (m[3,2]=2) then begin m[3,1]:=1; vyvod; proverka; end;
          if (m[3,1]=2) then
            begin
              m[3,2]:=1;
              WaR;
              if (m[1,1]=2) or (m[2,1]=2) then begin m[1,2]:=1; vyvod; proverka; end;
              if (m[1,2]=2) then begin m[1,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[3,1]=2) then 
        begin
          m[3,2]:=1;
          WaR;
          if (m[1,1]=2) or (m[2,1]=2) or (m[1,3]=2) or (m[2,3]=2) then begin m[1,2]:=1; vyvod; proverka; end;
          if (m[1,2]=2) then
            begin
              m[2,3]:=1;
              WaR;
              if (m[1,1]=2) or (m[1,3]=2) then begin m[2,1]:=1; vyvod; proverka; end;
              if (m[2,1]=2) then begin m[1,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[3,2]=2) then 
        begin
          m[3,1]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,2]=2) or (m[2,1]=2) or (m[2,3]=2) then begin m[1,3]:=1; vyvod; proverka; end;
          if (m[1,3]=2) then
            begin
              m[2,3]:=1;
              WaR;
              if (m[1,1]=2) or (m[1,2]=2) then begin m[2,1]:=1; vyvod; proverka; end;
              if (m[2,1]=2) then begin m[1,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
    end;
  if (m[2,1]=2) then 
    begin
      m[2,2]:=1;
      WaR;
      if (m[1,1]=2) then 
        begin
          m[3,1]:=1;
          WaR;
          if (m[1,2]=2) or (m[2,3]=2) or (m[3,2]=2) or (m[3,3]=2) then begin m[1,3]:=1; vyvod; proverka; end;
          if (m[1,3]=2) then
            begin
              m[1,2]:=1;
              WaR;
              if (m[2,3]=2) or (m[3,3]=2) then begin m[3,2]:=1; vyvod; proverka; end;
              if (m[3,2]=2) then begin m[3,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[1,2]=2) then 
        begin
          m[1,1]:=1;
          WaR;
          if (m[3,1]=2) or (m[3,2]=2) or (m[1,3]=2) or (m[2,3]=2) then begin m[3,3]:=1; vyvod; proverka; end;
          if (m[3,3]=2) then
            begin
              m[1,3]:=1;
              WaR;
              if (m[2,3]=2) or (m[3,2]=2) then begin m[3,1]:=1; vyvod; proverka; end;
              if (m[3,1]=2) then begin m[3,2]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[1,3]=2) then 
        begin
          m[1,2]:=1;
          WaR;
          if (m[1,1]=2) or (m[2,3]=2) or (m[3,1]=2) or (m[3,3]=2) then begin m[3,2]:=1; vyvod; proverka; end;
          if (m[3,2]=2) then
            begin
              m[3,3]:=1;
              WaR;
              if (m[3,1]=2) or (m[2,3]=2) then begin m[1,1]:=1; vyvod; proverka; end;
              if (m[1,1]=2) then begin m[3,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[2,3]=2) then 
        begin
          m[1,1]:=1;
          WaR;
          if (m[1,2]=2) or (m[1,3]=2) or (m[3,1]=2) or (m[3,2]=2) then begin m[3,3]:=1; vyvod; proverka; end;
          if (m[3,3]=2) then
            begin
              m[1,3]:=1;
              WaR;
              if (m[3,1]=2) or (m[3,2]=2) then begin m[1,2]:=1; vyvod; proverka; end;
              if (m[1,2]=2) then begin m[3,1]:=1; vyvod; proverka; end;
            end;
        end;
      if (m[3,1]=2) then 
        begin
          m[1,1]:=1;
          WaR;
          if (m[1,2]=2) or (m[1,3]=2) or (m[3,2]=2) or (m[3,3]=2) then begin m[3,3]:=1; vyvod; proverka; end;
          if (m[3,3]=2) then
            begin
              m[3,2]:=1;
              WaR;
              if (m[1,3]=2) or (m[2,3]=2) then begin m[1,2]:=1; vyvod; proverka; end;
              if (m[1,2]=2) then begin m[1,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[3,2]=2) then 
        begin
          m[3,1]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,2]=2) or (m[3,1]=2) or (m[2,3]=2) then begin m[1,3]:=1; vyvod; proverka; end;
          if (m[1,3]=2) then
            begin
              m[1,1]:=1;
              WaR;
              if (m[1,2]=2) or (m[2,3]=2) then begin m[3,3]:=1; vyvod; proverka; end;
              if (m[3,3]=2) then begin m[2,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[3,3]=2) then 
        begin
          m[3,2]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,3]=2) or (m[2,3]=2) or (m[3,1]=2) then begin m[1,2]:=1; vyvod; proverka; end;
          if (m[1,2]=2) then
            begin
              m[1,3]:=1;
              WaR;
              if (m[2,3]=2) or (m[1,1]=2) then begin m[3,1]:=1; vyvod; proverka; end;
              if (m[3,1]=2) then begin m[1,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
    end;
  if (m[1,2]=2) then 
    begin
      m[2,2]:=1;
      WaR;
      if (m[1,1]=2) then 
        begin
          m[1,3]:=1;
          WaR;
          if (m[2,1]=2) or (m[2,3]=2) or (m[3,2]=2) or (m[3,3]=2) then begin m[3,1]:=1; vyvod; proverka; end;
          if (m[3,1]=2) then
            begin
              m[2,1]:=1;
              WaR;
              if (m[3,2]=2) or (m[3,3]=2) then begin m[2,3]:=1; vyvod; proverka; end;
              if (m[2,3]=2) then begin m[3,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[1,3]=2) then 
        begin
          m[1,1]:=1;
          WaR;
          if (m[2,1]=2) or (m[2,3]=2) or (m[3,1]=2) or (m[3,2]=2) then begin m[3,3]:=1; vyvod; proverka; end;
          if (m[3,3]=2) then
            begin
              m[3,2]:=1;
              WaR;
              if (m[3,1]=2) or (m[3,2]=2) then begin m[2,1]:=1; vyvod; proverka; end;
              if (m[2,1]=2) then begin m[3,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[2,1]=2) then 
        begin
          m[1,1]:=1;
          WaR;
          if (m[3,1]=2) or (m[3,2]=2) or (m[1,3]=2) or (m[2,3]=2) then begin m[3,3]:=1; vyvod; proverka; end;
          if (m[3,3]=2) then
            begin
              m[1,3]:=1;
              WaR;
              if (m[3,2]=2) or (m[2,3]=2) then begin m[3,1]:=1; vyvod; proverka; end;
              if (m[3,1]=2) then begin m[3,2]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[2,3]=2) then 
        begin
          m[1,3]:=1;
          WaR;
          if (m[1,1]=2) or (m[2,1]=2) or (m[3,2]=2) or (m[3,3]=2) then begin m[3,1]:=1; vyvod; proverka; end;
          if (m[3,1]=2) then
            begin
              m[1,1]:=1;
              WaR;
              if (m[2,1]=2) or (m[3,2]=2) then begin m[3,3]:=1; vyvod; proverka; end;
              if (m[3,3]=2) then begin m[3,2]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[3,1]=2) then 
        begin
          m[2,1]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,3]=2) or (m[3,2]=2) or (m[3,3]=2) then begin m[2,3]:=1; vyvod; proverka; end;
          if (m[2,3]=2) then
            begin
              m[3,3]:=1;
              WaR;
              if (m[1,3]=2) or (m[3,2]=2) then begin m[1,1]:=1; vyvod; proverka; end;
              if (m[1,1]=2) then begin m[1,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[3,2]=2) then 
        begin
          m[3,3]:=1;
          WaR;
          if (m[1,3]=2) or (m[2,3]=2) or (m[2,1]=2) or (m[3,1]=2) then begin m[1,1]:=1; vyvod; proverka; end;
          if (m[1,1]=2) then
            begin
              m[1,3]:=1;
              WaR;
              if (m[2,1]=2) or (m[3,1]=2) then begin m[2,3]:=1; vyvod; proverka; end;
              if (m[2,3]=2) then begin m[3,1]:=1; vyvod; proverka; end;
            end;
        end;
      if (m[3,3]=2) then 
        begin
          m[2,2]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,3]=2) or (m[3,1]=2) or (m[3,2]=2) then begin m[2,1]:=1; vyvod; proverka; end;
          if (m[2,1]=2) then
            begin
              m[3,1]:=1;
              WaR;
              if (m[1,1]=2) or (m[3,2]=2) then begin m[1,3]:=1; vyvod; proverka; end;
              if (m[1,3]=2) then begin m[1,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
    end;
  if (m[2,3]=2) then 
    begin
      m[2,2]:=1;
      WaR;
      if (m[1,1]=2) then 
        begin
          m[1,2]:=1;
          WaR;
          if (m[1,3]=2) or (m[2,1]=2) or (m[3,1]=2) or (m[3,3]=2) then begin m[3,2]:=1; vyvod; proverka; end;
          if (m[3,2]=2) then
            begin
              m[3,1]:=1;
              WaR;
              if (m[2,1]=2) or (m[3,3]=2) then begin m[1,3]:=1; vyvod; proverka; end;
              if (m[1,3]=2) then begin m[3,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[1,2]=2) then 
        begin
          m[1,3]:=1;
          WaR;
          if (m[1,1]=2) or (m[2,1]=2) or (m[3,2]=2) or (m[3,3]=2) then begin m[3,1]:=1; vyvod; proverka; end;
          if (m[3,1]=2) then
            begin
              m[1,1]:=1;
              WaR;
              if (m[2,1]=2) or (m[3,2]=2) then begin m[3,3]:=1; vyvod; proverka; end;
              if (m[3,3]=2) then begin m[3,2]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[1,3]=2) then 
        begin
          m[3,3]:=1;
          WaR;
          if (m[1,2]=2) or (m[2,1]=2) or (m[3,1]=2) or (m[3,2]=2) then begin m[1,1]:=1; vyvod; proverka; end;
          if (m[1,1]=2) then
            begin
              m[1,2]:=1;
              WaR;
              if (m[2,1]=2) or (m[3,1]=2) then begin m[3,2]:=1; vyvod; proverka; end;
              if (m[3,2]=2) then begin m[3,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[2,1]=2) then 
        begin
          m[1,3]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,2]=2) or (m[3,2]=2) or (m[3,3]=2) then begin m[3,1]:=1; vyvod; proverka; end;
          if (m[3,1]=2) then
            begin
              m[1,1]:=1;
              WaR;
              if (m[1,2]=2) or (m[3,2]=2) then begin m[3,3]:=1; vyvod; proverka; end;
              if (m[3,3]=2) then begin m[1,2]:=1; vyvod; proverka; end;
            end;
        end;
      if (m[3,1]=2) then 
        begin
          m[3,2]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,3]=2) or (m[2,1]=2) or (m[3,3]=2) then begin m[1,2]:=1; vyvod; proverka; end;
          if (m[1,2]=2) then
            begin
              m[1,1]:=1;
              WaR;
              if (m[2,1]=2) or (m[1,3]=2) then begin m[3,3]:=1; vyvod; proverka; end;
              if (m[3,3]=2) then begin m[1,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[3,2]=2) then 
        begin
          m[3,3]:=1;
          WaR;
          if (m[1,2]=2) or (m[1,3]=2) or (m[2,1]=2) or (m[3,1]=2) then begin m[1,1]:=1; vyvod; proverka; end;
          if (m[1,1]=2) then
            begin
              m[3,1]:=1;
              WaR;
              if (m[2,1]=2) or (m[1,2]=2) then begin m[1,3]:=1; vyvod; proverka; end;
              if (m[1,3]=2) then begin m[1,2]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[3,3]=2) then 
        begin
          m[1,3]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,2]=2) or (m[2,1]=2) or (m[3,2]=2) then begin m[3,1]:=1; vyvod; proverka; end;
          if (m[3,1]=2) then
            begin
              m[3,2]:=1;
              WaR;
              if (m[1,1]=2) or (m[2,1]=2) then begin m[1,2]:=1; vyvod; proverka; end;
              if (m[1,2]=2) then begin m[1,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
    end;
  if (m[3,2]=2) then 
    begin
      m[2,2]:=1;
      WaR;
      if (m[1,1]=2) then 
        begin
          m[2,1]:=1;
          WaR;
          if (m[1,2]=2) or (m[1,3]=2) or (m[3,1]=2) or (m[3,3]=2) then begin m[2,3]:=1; vyvod; proverka; end;
          if (m[2,3]=2) then
            begin
              m[1,3]:=1;
              WaR;
              if (m[1,2]=2) or (m[3,3]=2) then begin m[3,1]:=1; vyvod; proverka; end;
              if (m[3,1]=2) then begin m[3,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[1,2]=2) then 
        begin
          m[1,1]:=1;
          WaR;
          if (m[1,3]=2) or (m[2,1]=2) or (m[2,3]=2) or (m[3,1]=2) then begin m[3,3]:=1; vyvod; proverka; end;
          if (m[3,3]=2) then
            begin
              m[3,1]:=1;
              WaR;
              if (m[1,3]=2) or (m[2,3]=2) then begin m[2,1]:=1; vyvod; proverka; end;
              if (m[2,1]=2) then begin m[1,3]:=1; vyvod; proverka; end;
            end;
        end;
      if (m[1,3]=2) then 
        begin
          m[2,3]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,2]=2) or (m[3,1]=2) or (m[3,3]=2) then begin m[2,1]:=1; vyvod; proverka; end;
          if (m[2,1]=2) then
            begin
              m[1,1]:=1;
              WaR;
              if (m[1,2]=2) or (m[3,1]=2) then begin m[3,3]:=1; vyvod; proverka; end;
              if (m[3,3]=2) then begin m[3,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[2,1]=2) then 
        begin
          m[3,1]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,2]=2) or (m[2,3]=2) or (m[3,3]=2) then begin m[1,3]:=1; vyvod; proverka; end;
          if (m[1,3]=2) then
            begin
              m[3,3]:=1;
              WaR;
              if (m[1,2]=2) or (m[2,3]=2) then begin m[1,1]:=1; vyvod; proverka; end;
              if (m[1,1]=2) then begin m[1,2]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[2,3]=2) then 
        begin
          m[3,3]:=1;
          WaR;
          if (m[1,3]=2) or (m[1,2]=2) or (m[2,1]=2) or (m[3,1]=2) then begin m[1,1]:=1; vyvod; proverka; end;
          if (m[1,1]=2) then
            begin
              m[3,1]:=1;
              WaR;
              if (m[1,2]=2) or (m[2,1]=2) then begin m[1,3]:=1; vyvod; proverka; end;
              if (m[1,3]=2) then begin m[1,2]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[3,1]=2) then 
        begin
          m[3,3]:=1;
          WaR;
          if (m[1,2]=2) or (m[1,3]=2) or (m[2,1]=2) or (m[2,3]=2) then begin m[1,1]:=1; vyvod; proverka; end;
          if (m[1,1]=2) then
            begin
              m[2,1]:=1;
              WaR;
              if (m[1,2]=2) or (m[1,3]=2) then begin m[2,3]:=1; vyvod; proverka; end;
              if (m[2,3]=2) then begin m[1,3]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
      if (m[3,3]=2) then 
        begin
          m[3,1]:=1;
          WaR;
          if (m[1,1]=2) or (m[1,2]=2) or (m[2,1]=2) or (m[2,3]=2) then begin m[1,3]:=1; vyvod; proverka; end;
          if (m[1,3]=2) then
            begin
              m[2,3]:=1;
              WaR;
              if (m[1,1]=2) or (m[1,2]=2) then begin m[2,1]:=1; vyvod; proverka; end;
              if (m[2,1]=2) then begin m[1,1]:=1; WaR; vyvod; writeln; writeln ('Ничья'); end;
            end;
        end;
    end;
end else 
begin
WaR;
vyvod;
WaR;
vyvod;
randomize;
igr:=random (7);
case igr of
  1: begin m[1,1]:=1; m[1,2]:=1; m[1,3]:=1; end;
  2: begin m[2,1]:=1; m[2,2]:=1; m[2,3]:=1; end;
  3: begin m[3,1]:=1; m[3,2]:=1; m[3,3]:=1; end;
  4: begin m[1,1]:=1; m[2,1]:=1; m[3,1]:=1; end;
  5: begin m[1,2]:=1; m[2,2]:=1; m[3,2]:=1; end;
  6: begin m[1,3]:=1; m[2,3]:=1; m[3,3]:=1; end;
  7: begin m[1,1]:=1; m[2,2]:=1; m[3,3]:=1; end;
  0: begin m[3,1]:=1; m[2,2]:=1; m[1,3]:=1; end;
end;
vyvod;
proverka;
end;
end.
