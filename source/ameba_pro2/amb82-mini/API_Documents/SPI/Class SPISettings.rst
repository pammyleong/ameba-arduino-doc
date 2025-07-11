Class SPISettings
=================

.. contents::
  :local:
  :depth: 2

**SPISettings Class**
---------------------

**Description**
~~~~~~~~~~~~~~~

A class to set SPI parameters.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    class SPISettings

**Members**
~~~~~~~~~~~

+-------------------------------+--------------------------------------------------+
| **Public Constructors**                                                          |
+===============================+==================================================+
| SPISettings::SPISettings      | Create a SPISettings object and set SPI clock    |
|                               | speed, bit order and data mode                   |
+-------------------------------+--------------------------------------------------+

**SPISettings::SPISettings**
----------------------------

**Description**
~~~~~~~~~~~~~~~

Construct an object and configure SPI parameters — clock speed, bit order and data mode to the preferred default value.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    SPISettings(uint32_t clock, BitOrder bitOrder, uint8_t dataMode)

**Parameters**
~~~~~~~~~~~~~~

clock: SPI clock speed in Hz. Default value is 4000000.

bitOrder: The bit order of transmitting command/address/data. Default value is MSBFIRST.

- MSBFIRST (MSB: Most Significant Bit)

- LSBFIRST (LSB: Least Significant Bit)

dataMode: SPI has four modes that correspond to the four possible clocking configurations. Default value is SPI_MODE0.

- SPI_MODE0, SPI_MODE1, SPI_MODE2, SPI_MODE3

**Returns**
~~~~~~~~~~~

NA

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: This class seldom used alone, it is always used with beginTransaction() as a parameter in SPIClass. "SPI.h" must be included to use the class function.

**SPIClass Class**
------------------

**Description**
~~~~~~~~~~~~~~~

A class of SPI implementation for Ameba.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    class SPIClass

**Members**
~~~~~~~~~~~

+---------------------------------+------------------------------------------+
| **Public Constructors**                                                    |
+=================================+==========================================+
| SPIClass::SPIClass              | Constructs an SPI object                 |
+---------------------------------+------------------------------------------+
| **Public Methods**                                                         |
+---------------------------------+------------------------------------------+
| SPIClass::begin                 | Initialise SPI pins on Ameba board       |
+---------------------------------+------------------------------------------+
| SPIClass::transfer              | Transfer data through SPI                |
+---------------------------------+------------------------------------------+
| SPIClass::transfer16            | Transfer data of 16-bits through SPI     |
+---------------------------------+------------------------------------------+
| SPIClass::beginTransaction      | Set slave select pin and SPI initial     |
|                                 | settings                                 |
+---------------------------------+------------------------------------------+
| SPIClass::endTransaction        | Stop SPI transaction                     |
+---------------------------------+------------------------------------------+
| SPIClass::setBitOrder           | Set bit order to either MSB first or LSB |
|                                 | first                                    |
+---------------------------------+------------------------------------------+
| SPIClass::setDataMode           | Set data mode                            |
+---------------------------------+------------------------------------------+
| SPIClass::setClockDivider       | Set to correct clock speed (no effect on |
|                                 | Ameba)                                   |
+---------------------------------+------------------------------------------+
| SPIClass::setDefaultFrequency   | Set default SPI frequency                |
+---------------------------------+------------------------------------------+
| SPIClass::end                   | Stop SPI master mode                     |
+---------------------------------+------------------------------------------+
| SPIClass::slaveRead             | Slave receive one frame use SPI          |
+---------------------------------+------------------------------------------+
| SPIClass::slaveWrite            | Slave send one frame use SPI             |
+---------------------------------+------------------------------------------+
| SPIClass::masterWrite           | Master send one frame use SPI            |
+---------------------------------+------------------------------------------+
| SPIClass::pSpiMaster            | Pointer of SPI master project            |
+---------------------------------+------------------------------------------+
| SPIClass::pSpiSlave             | Pointer of SPI slave project             |
+---------------------------------+------------------------------------------+

**SPIClass::SPIClass**
----------------------

**Description**
~~~~~~~~~~~~~~~

Construct an SPI object, create a pointer to the SPI master object, and assign "MOSI, MISO, CLK, and SS" to the corresponding pins on Ameba boards. Default SPI transmission frequency is set to 20,000,000 Hz.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    SPIClass(void *pSpiObj, int mosi, int miso, int clk, int ss);

**Parameters**
~~~~~~~~~~~~~~

pSpiObj: A pointer to a structure that stores SPI configuration.

mosi: Master Out, Slave In, a.k.a. Data transmission from a Host to Device.

miso: Master In, Slave Out, a.k.a. Data transmission from a Device to Host.

clk: Serial Clock. Oscillating signal generated by a Host that keeps the transmission of data bits in sync.

ss: Slave Select. Allows a Host to select individual Device(s) connected to the bus in order to send or receive data.

**Returns**
~~~~~~~~~~~

NA

**Example Code**
~~~~~~~~~~~~~~~~

Example: `LCD_Screen_ILI9341_TFT <https://github.com/Ameba-AIoT/ameba-arduino-pro2/blob/dev/Arduino_package/hardware/libraries/SPI/examples/LCD_Screen_ILI9341_TFT/LCD_Screen_ILI9341_TFT.ino>`_

.. note :: Depending on the Ameba hardware, up to 2 SPIClass objects are created in the spi.cpp library, please use "SPI" for first hardware SPI object and "SPI1" for the second. "SPI.h" must be included to use the class function.

**SPIClass::begin**
-------------------

**Description**
~~~~~~~~~~~~~~~

Initialize MOSI, MISO, CLK, and SS pins on Ameba boards, select SPIClass object, and set SPI format and frequency.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    void begin(void);
    void begin(int ss);

**Parameters**
~~~~~~~~~~~~~~

ss: Slave Select. Allows a Host to select individual Device(s) connected to the bus in order to send or receive data.

**Returns**
~~~~~~~~~~~

NA

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: This is a required method to use SPI on Ameba. "SPI.h" must be included to use the class function.

**SPIClass::transfer**
----------------------

**Description**
~~~~~~~~~~~~~~~

Transfer data through SPI to the slave.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    byte transfer(byte _pin, uint8_t _data, SPITransferMode _mode = SPI_LAST);
    byte transfer(uint8_t _data, SPITransferMode _mode = SPI_LAST);
    void transfer(byte _pin, void *_buf, size_t _count, SPITransferMode _mode = SPI_LAST);
    void transfer(void *_buf, size_t _count, SPITransferMode _mode = SPI_LAST);

**Parameters**
~~~~~~~~~~~~~~

_pin: Slave Select pin

_data: Data of 8-bits that transfer from SPI master to the slave

_buf: Data buffer stores data to be written to Tx FIFO

_mode: defines SS pin status after data transmission is finished, available values are SPI_CONTINUE and SPI_LAST. SPI_LAST indicates SS pin will be set to 1 upon data transmission ends.

_count: number of data bytes to be send

**Returns**
~~~~~~~~~~~

This function either returns NA or data of 8-bits that transferred through SPI master to the slave.

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: "SPI.h" must be included to use the class function.

**SPIClass::transfer16**
------------------------

**Description**
~~~~~~~~~~~~~~~

Transfer data of 16-bits through SPI master to the slave.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    uint16_t transfer16(byte _pin, uint16_t _data, SPITransferMode _mode = SPI_LAST);
    uint16_t transfer16(uint16_t _data, SPITransferMode _mode = SPI_LAST);

**Parameters**
~~~~~~~~~~~~~~

_pin: Slave Select pin

_data: Data of 16-bits that transfer from SPI master to the slave

_mode: defines SS pin status after data transmission is finished, available values are SPI_CONTINUE and SPI_LAST. SPI_LAST indicates SS pin will be set to 1 upon data transmission ends.

**Returns**
~~~~~~~~~~~

This function returns data of 16-bits being transferred.

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: "SPI.h" must be included to use the class function.

**SPIClass::beginTransaction**
------------------------------

**Description**
~~~~~~~~~~~~~~~

Set Slave Select pin and initialize SPI with default settings including SPI format, SPI frequency that have been declared in the SPISettings class.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    void beginTransaction(uint8_t pin, SPISettings settings);
    void beginTransaction(SPISettings settings);

**Parameters**
~~~~~~~~~~~~~~

pin: Slave Select pin

settings: an object of SPISettings class defined previously

**Returns**
~~~~~~~~~~~

NA

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: Refer to SPISettings class for details of the initial settings. "SPI.h" must be included to use the class function.

**SPIClass::endTransaction**
----------------------------

**Description**
~~~~~~~~~~~~~~~

Set Slave Select pin to 1 for ending the SPI transaction process.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    void endTransaction(void);

**Parameters**
~~~~~~~~~~~~~~

NA

**Returns**
~~~~~~~~~~~

NA

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: "SPI.h" must be included to use the class function.

**SPIClass::setBitOrder**
-------------------------

**Description**
~~~~~~~~~~~~~~~

Set bit order to either MSB first or LSB first and set slave select pin.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    void setBitOrder(uint8_t _pin, BitOrder _bitOrder);
    void setBitOrder(BitOrder _order);

**Parameters**
~~~~~~~~~~~~~~

_pin: slave select

_bitOrder: The bit order of transmitting command/address/data. Default value is MSBFIRST.

- MSBFIRST (MSB: Most Significant Bit)

- LSBFIRST (LSB: Least Significant Bit)

_order: same as _bitOrder. Default value is MSBFIRST.

**Returns**
~~~~~~~~~~~

NA

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: "SPI.h" must be included to use the class function.

**SPIClass::setDataMode**
-------------------------

**Description**
~~~~~~~~~~~~~~~

Set SPI data mode. A total of 4 modes and set slave select pin.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    void SPIClass::setDataMode(uint8_t _pin, uint8_t _mode);
    void SPIClass::setDataMode(uint8_t _mode);

**Parameters**
~~~~~~~~~~~~~~

_pin: Slave Select pin

_mode: SPI has four modes that correspond to the four possible clocking configurations. Default value is SPI_MODE0.

- SPI_MODE0, SPI_MODE1, SPI_MODE2, SPI_MODE3

**Returns**
~~~~~~~~~~~

NA

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: "SPI.h" must be included to use the class function.

**SPIClass::setClockDivider**
-----------------------------

**Description**
~~~~~~~~~~~~~~~

Set clock divider in order to get correct clock speed.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    void setClockDivider(uint8_t _pin, uint8_t _divider);
    void setClockDivider(uint8_t _div);

**Parameters**
~~~~~~~~~~~~~~

_pin: Slave Select pin

_divider: clock divider

_div: clock divider

**Returns**
~~~~~~~~~~~

NA

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: This function does not affect the Ameba board. "SPI.h" must be included to use the class function.

**SPIClass::setDefaultFrequency**
---------------------------------

**Description**
~~~~~~~~~~~~~~~

Set default SPI frequency.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    void setDefaultFrequency(int _frequency);

**Parameters**
~~~~~~~~~~~~~~

_frequency: the default SPI frequency in Hz. Default value is 20000000.

**Returns**
~~~~~~~~~~~

NA

**Example Code**
~~~~~~~~~~~~~~~~

Example: `LCD_Screen_ILI9341_TFT <https://github.com/Ameba-AIoT/ameba-arduino-pro2/blob/dev/Arduino_package/hardware/libraries/SPI/examples/LCD_Screen_ILI9341_TFT/LCD_Screen_ILI9341_TFT.ino>`_

.. note :: Take note that defaultFrequency = _frequency. "SPI.h" must be included to use the class function.

**SPIClass::end**
-----------------

**Description**
~~~~~~~~~~~~~~~

This function will finish the communication and release all the allocated resources to stop SPI master mode.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    void end(void);

**Parameters**
~~~~~~~~~~~~~~

NA

**Returns**
~~~~~~~~~~~

NA

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: After calling end(), you need to use begin() again to enable SPI function. "SPI.h" must be included to use the class function.

**SPIClass::slaveRead**
-----------------------

**Description**
~~~~~~~~~~~~~~~

This function retrieves data from receive buffer as slave. Slave receive one frame use SPI.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    int slaveRead(void);

**Parameters**
~~~~~~~~~~~~~~

NA

**Returns**
~~~~~~~~~~~

This function returns the data received from master.

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: "SPI.h" must be included to use the class function.

**SPIClass::slaveWrite**
------------------------

**Description**
~~~~~~~~~~~~~~~

This function use slave send one frame use SPI.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    void slaveWrite(int value);
    void slaveWrite(spi_t *pSpiObj, int value);

**Parameters**
~~~~~~~~~~~~~~

value: the data to transmit

pSpiObj: spi slave object define in application software

**Returns**
~~~~~~~~~~~

NA

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: "SPI.h" must be included to use the class function.

**SPIClass::masterWrite**
-------------------------

**Description**
~~~~~~~~~~~~~~~

This function use master send one frame use SPI.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    int masterWrite(int value);

**Parameters**
~~~~~~~~~~~~~~

value: the data to transmit

**Returns**
~~~~~~~~~~~

This function returns the data received from slave.

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: "SPI.h" must be included to use the class function.

**SPIClass::pSpiMaster**
------------------------

**Description**
~~~~~~~~~~~~~~~

It is a pointer of SPI master project.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    spi_t *pSpiMaster;

**Parameters**
~~~~~~~~~~~~~~

NA

**Returns**
~~~~~~~~~~~

NA

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: "SPI.h" must be included to use the class function.

**SPIClass::pSpiMaster**
------------------------

**Description**
~~~~~~~~~~~~~~~

It is a pointer of SPI slave project.

**Syntax**
~~~~~~~~~~

.. code-block:: c++

    spi_t *pSpiSlave;

**Parameters**
~~~~~~~~~~~~~~

NA

**Returns**
~~~~~~~~~~~

NA

**Example Code**
~~~~~~~~~~~~~~~~

NA

.. note :: "SPI.h" must be included to use the class function.
