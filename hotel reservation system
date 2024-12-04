import java.awt.*;
import java.awt.event.*;
import java.util.ArrayList;

public class HotelReservationSystem extends Frame implements ActionListener {
    private TextField tfName, tfRoomNumber;
    private TextArea taBookings;
    private Button btnBook, btnShowBookings, btnClear;
    private List availableRooms;

    private ArrayList<String> bookings = new ArrayList<>();

    public HotelReservationSystem() {
        setTitle("Hotel Reservation System");
        setSize(600, 400);
        setLayout(new BorderLayout());

        // Header
        Label header = new Label("Hotel Reservation System", Label.CENTER);
        header.setFont(new Font("Arial", Font.BOLD, 20));
        add(header, BorderLayout.NORTH);

        // Form Panel
        Panel formPanel = new Panel(new GridLayout(5, 2, 10, 10));

        formPanel.add(new Label("Name:"));
        tfName = new TextField();
        formPanel.add(tfName);

        formPanel.add(new Label("Room Number:"));
        tfRoomNumber = new TextField();
        formPanel.add(tfRoomNumber);

        formPanel.add(new Label("Available Rooms:"));
        availableRooms = new List();
        populateAvailableRooms();
        formPanel.add(availableRooms);

        btnBook = new Button("Book Room");
        btnBook.addActionListener(this);
        formPanel.add(btnBook);

        btnClear = new Button("Clear Fields");
        btnClear.addActionListener(this);
        formPanel.add(btnClear);

        add(formPanel, BorderLayout.CENTER);

        // Bookings Area
        taBookings = new TextArea();
        taBookings.setEditable(false);
        add(taBookings, BorderLayout.SOUTH);

        btnShowBookings = new Button("Show All Bookings");
        btnShowBookings.addActionListener(this);
        add(btnShowBookings, BorderLayout.EAST);

        // Window Closing Event
        addWindowListener(new WindowAdapter() {
            public void windowClosing(WindowEvent we) {
                System.exit(0);
            }
        });

        setVisible(true);
    }

    private void populateAvailableRooms() {
        for (int i = 101; i <= 110; i++) {
            availableRooms.add("Room " + i);
        }
    }

    public void actionPerformed(ActionEvent ae) {
        if (ae.getSource() == btnBook) {
            String name = tfName.getText().trim();
            String roomNumber = tfRoomNumber.getText().trim();

            if (name.isEmpty() || roomNumber.isEmpty()) {
                showMessage("Please fill in all fields.");
            } else {
                bookings.add("Name: " + name + ", Room: " + roomNumber);
                availableRooms.remove("Room " + roomNumber);
                taBookings.setText("Booking successful!\nName: " + name + "\nRoom: " + roomNumber);
                clearFields();
            }
        } else if (ae.getSource() == btnShowBookings) {
            if (bookings.isEmpty()) {
                taBookings.setText("No bookings available.");
            } else {
                taBookings.setText("All Bookings:\n");
                for (String booking : bookings) {
                    taBookings.append(booking + "\n");
                }
            }
        } else if (ae.getSource() == btnClear) {
            clearFields();
        }
    }

    private void clearFields() {
        tfName.setText("");
        tfRoomNumber.setText("");
    }

    private void showMessage(String message) {
        Dialog dialog = new Dialog(this, "Message", true);
        dialog.setLayout(new FlowLayout());
        dialog.add(new Label(message));
        Button btnOk = new Button("OK");
        btnOk.addActionListener(e -> dialog.setVisible(false));
        dialog.add(btnOk);
        dialog.setSize(300, 100);
        dialog.setVisible(true);
    }

    public static void main(String[] args) {
        new HotelReservationSystem();
    }
}
