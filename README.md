##  Примерна имплементация на криптовалута подкрепена и подплатена с фиатни резерви от единствената акредитирана за тази дейност институция - Българска Народна Банка.
  
### Защо е нужен Крипто Левът?
  
######  През последните месеци криптопазарите показаха огромния потенциал на технологията да преобрази както финансовите пазари, така и много неефективни бизнес модели и индустрии, в основата на които стои посредникът-арбитър на доверие. Спекулацията и последвалата волатилност обаче пречат и спъват развитието на търговията и финансовата предвдимост пред бизнесите, работещи с такива валути, а най-известното от решенията на този проблем Tether (USDT) се ползва с изключително ниско доверие в прозрачността, способностите и стимулите му да поддържа винаги 1:1 курс и ликвидност на USDT-USD. Нещо, което може да се гарантира единствено строго регуларана институция или самия Федерален Резерв на САЩ. 
######   Голяма част от пазара търси и спасение от самия долар в биткойн и останалите криптовалути и затова едно подобно таковаа решение от страна на Фед ще се посрещне най-вероятно с много силен скептицизъм. В същото време, една от най-напредналите в електронно отношение държави, Естония, изяви желание да направи такава валута, но заради факта, че използва еврото, тези планове бяха бързо покосени от Европейската Централна Банка, която консервативно отсече, че държавите-членки на еврозоната нямат право да издават и използват официално друга валута освен традиоционното евро. 
######   Ето защо тук се отваря една ниша, която левът и България, със своята независима БНБ, с фиксиран курс към еврото и част от най-напредналия икономически съюз в света, представляват тъй необходимият остров на стабилността и сигурността на финансовите крипто пазари. Чрез този ход, България има шанса да излезе в предните редици на държавите, които предоставят благоприятен климат за инвестиции и развитие на крипто технологии и стартъп идеи, наред с вече съществуващия силен ИТ клъстер в София. 
  
###  Q&A: Характеристики на примерната имплементация
  
  **Q: Какъв курс би имал Крипто Левът спрямо традиционния лев?**
  
  A: Курсът поддържан от БНБ ще е фиксиран завинаги 1:1. Всеки Крипто Лев е гарантиран, подкрепен от реални резерви и напълно ликвиден към традиционния лев в офисите на БНБ.
  
  **Q: Колко Крипто Лева ще има в обращение?**
  
  A: Също както при традиционния лев, количеството в обращение се определя от централната банка спрямо правилата на валутния борд, в които оперира.
  
  **Q: Как може да се закупят Крипто Левове? Може ли да се копаят?**
  
  A: Крипто Левовете могат да се закупят на фиксирания курс 1:1 към традиционния лев от офисите на БНБ при определни от БНБ правила и процедури. За разлика от останалите криптовалути, тази няма да може да се копае, защото няма да използва свой собствен блокчейн (повече подробности в техническите детайли).
  
  **Q: Има ли опасност Крипто Левовете да се изплзват за нелегална дейност, пране на пари или финансиране на тероризма, каквато е невъзможна с традиционни левове?**
  
  A: Освен че както при (почти) всяка друга криптовалута транзакциите са публични, при Крипто Лева самоличността на всеки първоизточник е ясен при закупуването от БНБ, както и при последващ опит да се обърне Крипто Лева в традиционнен лев - прозрачност, която напълно отсъства при традиционния лев.
   
  **Q: Вярно ли е, че няма да има такси за превод на Крипто Лева?**
  
  A: Сумата на транзакциите в Крипто Левове ще има 0% такса, т.е. колкото се изпратят, толкова и се получават, но ще е нужно да се плащат такси за транзакциите в Ethereum мрежата (текущата най-скалируема и в същото време с най-ниски такси блокчейн мрежа - може да проверите текущите такси тук: https://ethgasstation.info/ ).
  
  **Q: Каква ще е техническата имплементация на Крипто Лева?**
  
  A: Първоначалното предложение за имплементацията използва за основа OpenZeppelin имплементацията на ERC20 стандарта, който в последните месеци доста широко се изплзва направата на токъни за ICO-та, като текущата имплементацията надгражда единствено с възможност за БНБ да замразява определени сметки при съмнения за нелегална дейност или финансиране на тероризма, както и в краен случай да замразява изцяло търговията с Крипто Лева с цел да предпази притежателите от непредвидени технически проблеми. Кодът на иплементацията е изложен в отделна секция по-надолу.
   
  **Q: Какви предимства ще им Крипто Лева над традиционния?**
  
  A: Бивайки изграден на базата на Ethereum блокчейна, Крипто Левът наследява всички революционни свойства, които предлага Ethereum, а именно умните договори (smart contracts), децентрализирана търговия и такава без доверие между страните, ZKSNARKS, Lightning Network (скоро) и много други. Левът потенциално може широко да се приеме за резервна валута в криптотърговията, както и да привлече много инвеститори в страната ни.
  
# Примерна имплементация

```

  pragma solidity 0.4.19;

  /**
   * @title SafeMath
   * @dev Math operations with safety checks that throw on error
   */
  library SafeMath {
      function mul(uint256 a, uint256 b) internal pure returns (uint256) {
          uint256 c = a * b;
          require(a == 0 || c / a == b);
          return c;
      }

      function div(uint256 a, uint256 b) internal pure returns (uint256) {
          // assert(b > 0); // Solidity automatically throws when dividing by 0
          uint256 c = a / b;
          // assert(a == b * c + a % b); // There is no case in which this doesn't hold
          return c;
      }

      function sub(uint256 a, uint256 b) internal pure returns (uint256) {
          require(b <= a);
          return a - b;
      }

      function add(uint256 a, uint256 b) internal pure returns (uint256) {
          uint256 c = a + b;
          require(c >= a);
          return c;
      }
  }

  /**
   * @title ERC20Basic
   * @dev Simpler version of ERC20 interface
   * @dev see https://github.com/ethereum/EIPs/issues/179
   */
  contract ERC20Basic {
      uint256 public totalSupply;
      function balanceOf(address who) public view returns (uint256);
      function transfer(address to, uint256 value) public returns (bool);
      event Transfer(address indexed from, address indexed to, uint256 value);
  }

  /**
   * @title Basic token
   * @dev Basic version of StandardToken, with no allowances.
   */
  contract BasicToken is ERC20Basic {
      using SafeMath for uint256;

      mapping(address => uint256) public balances;

      /**
      * @dev transfer token for a specified address
      * @param _to The address to transfer to.
      * @param _value The amount to be transferred.
      */
      function transfer(address _to, uint256 _value) public returns (bool) {
          require(_to != address(0));
          require(_value <= balances[msg.sender]);

          // SafeMath.sub will throw if there is not enough balance.
          balances[msg.sender] = balances[msg.sender].sub(_value);
          balances[_to] = balances[_to].add(_value);
          Transfer(msg.sender, _to, _value);
          return true;
      }

      /**
      * @dev Gets the balance of the specified address.
      * @param _owner The address to query the the balance of.
      * @return An uint256 representing the amount owned by the passed address.
      */
      function balanceOf(address _owner) public view returns (uint256 balance) {
          return balances[_owner];
      }
  }

  /**
   * @title ERC20 interface
   * @dev see https://github.com/ethereum/EIPs/issues/20
   */
  contract ERC20 is ERC20Basic {
      function allowance(address owner, address spender) public view returns (uint256);
      function transferFrom(address from, address to, uint256 value) public returns (bool);
      function approve(address spender, uint256 value) public returns (bool);
      event Approval(address indexed owner, address indexed spender, uint256 value);
  }

  /**
   * @title SafeERC20
   * @dev Wrappers around ERC20 operations that throw on failure.
   * To use this library you can add a `using SafeERC20 for ERC20;` statement to your contract,
   * which allows you to call the safe operations as `token.safeTransfer(...)`, etc.
   */
  library SafeERC20 {
      function safeTransfer(ERC20Basic token, address to, uint256 value) internal {
          assert(token.transfer(to, value));
      }

      function safeTransferFrom(ERC20 token, address from, address to, uint256 value) internal {
          assert(token.transferFrom(from, to, value));
      }

      function safeApprove(ERC20 token, address spender, uint256 value) internal {
          assert(token.approve(spender, value));
      }
  }

  /**
   * @title Standard ERC20 token
   *
   * @dev Implementation of the basic standard token.
   * @dev https://github.com/ethereum/EIPs/issues/20
   * @dev Based on code by FirstBlood: https://github.com/Firstbloodio/token/blob/master/smart_contract/FirstBloodToken.sol
   */
  contract StandardToken is ERC20, BasicToken {

      mapping (address => mapping (address => uint256)) internal allowed;


      /**
       * @dev Transfer tokens from one address to another
       * @param _from address The address which you want to send tokens from
       * @param _to address The address which you want to transfer to
       * @param _value uint256 the amount of tokens to be transferred
       */
      function transferFrom(address _from, address _to, uint256 _value) public returns (bool) {
          require(_to != address(0));
          require(_value <= balances[_from]);
          require(_value <= allowed[_from][msg.sender]);

          balances[_from] = balances[_from].sub(_value);
          balances[_to] = balances[_to].add(_value);
          allowed[_from][msg.sender] = allowed[_from][msg.sender].sub(_value);
          Transfer(_from, _to, _value);
          return true;
      }

      /**
       * @dev Approve the passed address to spend the specified amount of tokens on behalf of msg.sender.
       *
       * Beware that changing an allowance with this method brings the risk that someone may use both the old
       * and the new allowance by unfortunate transaction ordering. One possible solution to mitigate this
       * race condition is to first reduce the spender's allowance to 0 and set the desired value afterwards:
       * https://github.com/ethereum/EIPs/issues/20#issuecomment-263524729
       * @param _spender The address which will spend the funds.
       * @param _value The amount of tokens to be spent.
       */
      function approve(address _spender, uint256 _value) public returns (bool) {
          allowed[msg.sender][_spender] = _value;
          Approval(msg.sender, _spender, _value);
          return true;
      }

      /**
       * @dev Function to check the amount of tokens that an owner allowed to a spender.
       * @param _owner address The address which owns the funds.
       * @param _spender address The address which will spend the funds.
       * @return A uint256 specifying the amount of tokens still available for the spender.
       */
      function allowance(address _owner, address _spender) public view returns (uint256 remaining) {
          return allowed[_owner][_spender];
      }

      /**
       * approve should be called when allowed[_spender] == 0. To increment
       * allowed value is better to use this function to avoid 2 calls (and wait until
       * the first transaction is mined)
       * From MonolithDAO Token.sol
       */
      function increaseApproval (address _spender, uint _addedValue) public returns (bool success) {
          allowed[msg.sender][_spender] = allowed[msg.sender][_spender].add(_addedValue);
          Approval(msg.sender, _spender, allowed[msg.sender][_spender]);
          return true;
      }

      function decreaseApproval (address _spender, uint _subtractedValue) public returns (bool success) {
          uint oldValue = allowed[msg.sender][_spender];
          if (_subtractedValue > oldValue) {
              allowed[msg.sender][_spender] = 0;
          } else {
              allowed[msg.sender][_spender] = oldValue.sub(_subtractedValue);
          }
          Approval(msg.sender, _spender, allowed[msg.sender][_spender]);
          return true;
      }
  }


  /**
   * @title Owned Token
   *
   * @dev owner should be an address solely owned by the Bulgarian National Bank (central bank of Bulgaria, EU)
   * per the implementation proposal on bulgariancryptolev.com
   */
  contract Owned {
      address public owner;

      function Owned() public {
          owner = msg.sender;
      }

      modifier onlyCentralBank {
          require(msg.sender == owner);
          _;
      }
  }

  contract BGN is StandardToken, Owned {
      string public constant name = "Bulgarian Lev";
      string public constant symbol = "BGN";
      uint8 public constant decimals = 2;

      mapping(address => bool) public ownerCanTrade;
      bool public tradingSuspended = false;

      function BGN () public {
      }

      function mint(address _beneficiary, uint256 _value) public onlyCentralBank returns (bool) {
          // increase currency total supply
          totalSupply = totalSupply.add(_value);
          // update the buyer's balance to number of tokens sent
          balances[_beneficiary] = balances[_beneficiary].add(_value);
      }

      function toggleTradingFrozen() public onlyCentralBank {
          tradingSuspended = !tradingSuspended;
      }

      function freezeAccount(address _owner) public onlyCentralBank {
          ownerCanTrade[_owner] = false;
      }

      function unfreezeAccount(address _owner) public onlyCentralBank {
          ownerCanTrade[_owner] = true;
      }

      function transfer(address _to, uint256 _value) public returns (bool) {
          if(!ownerCanTrade[msg.sender] && !tradingSuspended) return false;
          return BasicToken.transfer(_to,_value);
      }

      function transferFrom(address _from, address _to, uint256 _value) public returns (bool) {
          if(!ownerCanTrade[msg.sender] && !tradingSuspended) return false;
          return StandardToken.transferFrom(_from,_to,_value);
      }
  }


```

