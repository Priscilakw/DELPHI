unit Unit1;

interface

uses
  Winapi.Windows, Winapi.Messages, System.SysUtils, System.Variants, System.Classes, Vcl.Graphics,
  Vcl.Controls, Vcl.Forms, Vcl.Dialogs, Vcl.StdCtrls;

type
  TForm1 = class(TForm)
    EditValor: TEdit;
    BtnReceita: TButton;
    BtnDespesa: TButton;
    MemoTransacoes: TMemo;
    LabelSaldo: TLabel;
    procedure BtnReceitaClick(Sender: TObject);
    procedure BtnDespesaClick(Sender: TObject);
  private
    Saldo: Double;
  public
    { Public declarations }
  end;

var
  Form1: TForm1;

implementation

{$R *.dfm}

procedure TForm1.BtnReceitaClick(Sender: TObject);
var
  Valor: Double;
begin
  // Adiciona receita ao saldo
  Valor := StrToFloatDef(EditValor.Text, 0);
  Saldo := Saldo + Valor;

  // Exibe transação no Memo
  MemoTransacoes.Lines.Add(Format('Receita: +%.2f', [Valor]));

  // Atualiza o saldo exibido
  LabelSaldo.Caption := Format('Saldo: %.2f', [Saldo]);

  // Limpa o campo de entrada
  EditValor.Text := '';
end;

procedure TForm1.BtnDespesaClick(Sender: TObject);
var
  Valor: Double;
begin
  // Adiciona despesa ao saldo
  Valor := StrToFloatDef(EditValor.Text, 0);
  Saldo := Saldo - Valor;

  // Exibe transação no Memo
  MemoTransacoes.Lines.Add(Format('Despesa: -%.2f', [Valor]));

  // Atualiza o saldo exibido
  LabelSaldo.Caption := Format('Saldo: %.2f', [Saldo]);

  // Limpa o campo de entrada
  EditValor.Text := '';
end;

end.
